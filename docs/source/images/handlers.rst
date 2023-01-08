Handler Management
==================

Handlers (or listeners) are managed via the ``Handlers`` menu.  Each handler type can be accessed via each corresponding tab.

.. image:: /images/handlers/handlers.png

Click on the ``+`` button to add a handler of the selected type.

HTTP
----

The HTTP handler is an egress handler, and takes 4 options:

* Name

  * A unique name to identiy the handler.

* Bind Port

  * The port to bind to on the Team Server.  Useful if you want to bind to an odd port and redirect traffic using a redirector (iptables, apache, nginx, etc).

* Connect Address

  * The IP address or domain name that the implant will attempt to talk to.

* Connect Port

  * The port on which the implant will attempt to talk to.

.. image:: /images/handlers/http.png

.. note::
    There is currently no option exposed to enable HTTPS.

SMB
---

The SMB handler is a P2P handler, and takes 2 options:

* Name

  * A unique name to identiy the handler.

* Pipe Name

  * The named pipe name that will be bound on the endpoint.

.. image:: /images/handlers/smb.png

TCP
---

The TCP handler is a P2P handler, and takes 3 options:

* Name

  * A unique name to identiy the handler.

* Bind Port

  * The port to bind to.

* Localhost

  * Bind to the localhost only (``127.0.0.1``) or all interfaces (``0.0.0.0``).

.. image:: /images/handlers/tcp.png

EXTERNAL
--------

The External handler is an egress handler, and takes 2 options:

* Name

  * A unique name to identiy the handler.

* Bind Port

  * The Team Server will bind to this port and wait for a connection from a 3rd party controller.

.. image:: /images/handlers/ext.png