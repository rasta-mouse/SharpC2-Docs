Outgoing Webhooks
=================

Outgoing webhooks can be used to send SharpC2 :doc:`events` to external applications.

.. image:: /images/webhooks/no-webhooks.png

Slack
-----

The provided Slack consumer sends nicely formatted messages to your incoming Slack webhook URL.

.. image:: /images/webhooks/slack-hook.png
.. image:: /images/webhooks/slack-message.png

Custom
------

The custom consumer simply sends the events to the provided URL in JSON format.

.. image:: /images/webhooks/custom-hook.png

Here are some example events:

.. code-block:: json
    :caption: User Authentication

    {
        "id": "dd141bef5c",
        "nick": "rasta",
        "result": true,
        "date": "2023-04-30T11:57:28.3301882Z"
    }
    


.. code-block:: json
    :caption: Web Log
    
    {
        "id": "e485a45f5f",
        "method": "GET",
        "uri": "/webhook-test",
        "user_agent": "curl/8.0.1",
        "source_address": "127.0.0.1",
        "response_code": 404,
        "date": "2023-04-30T11:55:56.5781192Z"
    }