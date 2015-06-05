HitchRedis
==========

HitchRedis is a plugin for the Hitch testing framework that lets you run and
interact with Redis during your integration tests.


Use with Hitch
==============

Install like so::

    $ hitch install hitchredis


.. code-block:: python

        # Service definition in setup.py's setUp:
        self.services['Redis'] = hitchredis.RedisService(
            port=6379,
            version="2.8.4"
        )

        # Interact using the cli:
        self.services['Redis'].cli("-n", "1", "get", "mypasswd").run()


See this service in action at the DjangoRemindMe_ project.


Features
========

* Starts up on a separate thread in parallel with other services when running with HitchServe_, so that your integration tests run faster.
* Contains subcommand to interact with the CLI.
* Run the server on whatever port you like.
* Version must be set explicitly to prevent "works on my machine" screw ups caused by different versions of Redis being installed.


.. _HitchServe: https://github.com/crdoconnor/hitchserve
