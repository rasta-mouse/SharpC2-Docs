Interacting with Drones
=======================

The SharpC2 implant is called a "Drone".  Drones can be managed via the ``Drones`` menu.

.. image:: /images/drones/drones.png

The metadata information about the Drone is fairly self-explanatory.

The ``monitor`` icon is colour-coded based on the process integrity of the Drone.  Blue for Medium Integrity and Red for High Integrity.
It can also be clicked to quickly access common functionality such as modifying the sleep interval, killing the Drone, or removing it from the table.

Clicking the ``terminal`` icon will move you to a view where you can interact with that specific Drone.

The command textbox provides autocomplete behaviour when entering a command alias.

.. image:: /images/drones/autocomplete.png

The full command arguments are not entered into this text box.
Instead, select the command you want to use and a popup modal will prompt you for any required arguments and files.

.. image:: /images/drones/powershell.png

After submitting a command, it will appear in the main view.

.. image:: /images/drones/task-complete.png