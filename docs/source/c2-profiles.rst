C2 Profiles
===========

A C2 Profile can be used to customise/override default settings and behavours of the implant.  These currently only apply to the HTTP implant.  They are defined in YAML format and must be present in the team server's `C2Profiles` directory to be loaded.

HTTP
----

======     =====
Option     Description
======     =====
Sleep      The sleep interval of the implant in seconds
Jitter     The jitter of the sleep interval as a percentage
GetPaths   The URL paths to use on GET requests
PostPaths  The URL paths to use on POST requests
=====      =====

.. note::
    The GET and POST paths are selected randomly on each use.

Example Profile
---------------

.. code-block:: yaml

  Name: default
  Http:
    Sleep: 60
    Jitter: 10
    GetPaths:
      - /index.php
      - /news.php
    PostPaths:
      - /submit.php
      - /upload.php