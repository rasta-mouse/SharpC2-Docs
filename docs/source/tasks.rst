Tasks Status
============

Pending
-------

Whilst a task is ``Pending``, it is sat on the Team Server waiting for the associated Drone to check-in.  Once the Drone checks-in, the task will be delivered and its status will be updated to ``Tasked``.
You can "delete" a pending task before a Drone checks-in by clicking on the ``red cross`` icon.

.. image:: /images/tasks/pending.png


Running
-------

Tasks that are designed to run as background jobs will set the task status to ``Running`` once execution has begun.  These tasks can stream output as and when data is available.
You may cancel a running task by clicking on the ``yellow cross`` icon.

.. image:: /images/tasks/running.png


Complete
--------

Once a task reports that execution is complete, the task status will be updated to ``Complete``.

.. image:: /images/tasks/complete.png


Aborted
-------

Generally means that the task threw an exception.