Building
========

Team Server
-----------

Most people will want to build the Team Server for Linux and run it on an Ubuntu VM (or other distro.)

.. code-block::

   $ dotnet publish -c Release -r linux-x64 --self-contained

The ``--self-contained`` parameter is optional, but allows you to run the application without needing to have the .NET runtime installed.


Client
------

The .NET MAUI client can be built for `Windows <https://learn.microsoft.com/en-us/dotnet/maui/windows/deployment/publish-cli?view=net-maui-6.0>`_ and `macOS <https://learn.microsoft.com/en-us/dotnet/maui/macos/deployment/overview?view=net-maui-6.0>`_.