Running
=======

Team Server
-----------

Start the Team Server by proving the server's IP address and a shared password.  This IP address is used to generate a self-signed SSL certificate for the management API.

.. code-block::

    $ sudo ./TeamServer 172.19.51.165 Passw0rd!
    Certificate thumbprint: 7465758FA12F9122110D0821AD06CD426E29672C

Client
------

When connecting via the client, you'll be prompted to verify and accept the thumbprint of the Team Server.

.. image:: /images/running/client_thumbprint.png