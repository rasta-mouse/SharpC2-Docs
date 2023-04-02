Handler Management
==================

Handlers (or listeners) are managed via the ``Handlers`` menu.  Each handler type can be accessed via each corresponding tab.

.. image:: /images/handlers/handlers.png

Click on the ``+`` button to add a handler of the selected type.

HTTP
----

The HTTP handler is an egress handler, and has 4 options:

* Name

  * A unique name to identiy the handler.

* Bind Port

  * The port to bind to on the Team Server.  Useful if you want to bind to an odd port and redirect traffic using a redirector (iptables, apache, nginx, etc).

* Connect Address

  * The IP address or domain name that the implant will attempt to talk to.

* Connect Port

  * The port on which the implant will attempt to talk to.

.. image:: /images/handlers/http.png

HTTPS
-----

The HTTPS handler is an egress handler, and has 2 additional options:

* PFX Certificate

  * A certificate in PKCS #12 format.  If no certificate is provided, a self-signed certificate will be generated.

* PFX Password

  * If the PFX was generated with a password.

.. image:: /images/handlers/https.png


.. note::
    The current configuration is such that an HTTPS Drone will automatically accept any untrusted SSL certificate.

SMB
---

The SMB handler is a P2P handler, and has 2 options:

* Name

  * A unique name to identiy the handler.

* Pipe Name

  * The named pipe name that will be bound on the endpoint.

.. image:: /images/handlers/smb.png

TCP
---

The TCP handler is a P2P handler, and has 3 options:

* Name

  * A unique name to identiy the handler.

* Bind Port

  * The port to bind to.

* Localhost

  * Bind to the localhost only (``127.0.0.1``) or all interfaces (``0.0.0.0``).

.. image:: /images/handlers/tcp.png

EXTERNAL
--------

The External handler is an egress handler, and has 2 options:

* Name

  * A unique name to identiy the handler.

* Bind Port

  * The Team Server will bind to this port and wait for a connection from a 3rd party controller.

.. image:: /images/handlers/ext.png

See the :doc:`external-c2` page for more information on leverage this handler.