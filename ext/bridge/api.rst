.. currentmodule:: pycore

API Reference
=============

The reference manual that follows details the API of pycore's bridge command extension module.

.. note::

    Using the prefixed command version (which uses the ``ext.commands`` extension) of bridge
    commands in guilds requires :attr:`Intents.message_context` to be enabled.


.. _ext_bridge_api:

Bots
----

Bot
~~~

.. attributetable:: pycore.ext.bridge.Bot

.. autoclass:: pycore.ext.bridge.Bot
    :members:

    .. automethod:: Bot.add_bridge_command()

    .. automethod:: Bot.bridge_command()
        :decorator:

    .. automethod:: Bot.bridge_group()
        :decorator:

AutoShardedBot
~~~~~~~~~~~~~~

.. attributetable:: pycore.ext.bridge.AutoShardedBot

.. autoclass:: pycore.ext.bridge.AutoShardedBot
    :members:

Event Reference
---------------

These events function similar to :ref:`the regular events <pycore-api-events>`, except they
are custom to the bridge extension module.

.. function:: pycore.ext.bridge.on_bridge_command_error(ctx, error)

    An error handler that is called when an error is raised
    inside a command either through user input error, check
    failure, or an error in your own code.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`
    :param error: The error that was raised.
    :type error: :class:`.CommandError` derived

.. function:: pycore.ext.bridge.on_bridge_command(ctx)

    An event that is called when a command is found and is about to be invoked.

    This event is called regardless of whether the command itself succeeds via
    error or completes.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

.. function:: pycore.ext.bridge.on_bridge_command_completion(ctx)

    An event that is called when a command has completed its invocation.

    This event is called only if the command succeeded, i.e. all checks have
    passed and users input them correctly.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

Commands
--------

BridgeCommand
~~~~~~~~~~~~~

.. attributetable:: pycore.ext.bridge.BridgeCommand

.. autoclass:: pycore.ext.bridge.BridgeCommand
    :members:

BridgeCommandGroup
~~~~~~~~~~~~~~~~~~

.. attributetable:: pycore.ext.bridge.BridgeCommandGroup

.. autoclass:: pycore.ext.bridge.BridgeCommandGroup
    :members:

Decorators
~~~~~~~~~~
.. automethod:: pycore.ext.bridge.bridge_command()
    :decorator:

.. automethod:: pycore.ext.bridge.bridge_group()
    :decorator:

.. automethod:: pycore.ext.bridge.map_to()
    :decorator:

.. automethod:: pycore.ext.bridge.guild_only()
    :decorator:

.. automethod:: pycore.ext.bridge.is_nsfw()
    :decorator:

.. automethod:: pycore.ext.bridge.has_permissions()
    :decorator:

Command Subclasses
~~~~~~~~~~~~~~~~~~

.. autoclass:: pycore.ext.bridge.BridgeExtCommand

.. autoclass:: pycore.ext.bridge.BridgeExtGroup

.. autoclass:: pycore.ext.bridge.BridgeSlashCommand

.. autoclass:: pycore.ext.bridge.BridgeSlashGroup

Context
-------

BridgeContext
~~~~~~~~~~~~~

.. attributetable:: pycore.ext.bridge.BridgeContext

.. autoclass:: pycore.ext.bridge.BridgeContext
    :members:
    :exclude-members: _respond, _defer, _edit, _get_super

BridgeContext Subclasses
~~~~~~~~~~~~~~~~~~~~~~~~

.. attributetable:: pycore.ext.bridge.BridgeApplicationContext

.. autoclass:: pycore.ext.bridge.BridgeApplicationContext
    :members:

.. attributetable:: pycore.ext.bridge.BridgeExtContext

.. autoclass:: pycore.ext.bridge.BridgeExtContext
    :members:

.. attributetable:: pycore.ext.bridge.Context

.. data:: pycore.ext.bridge.Context

    Alias of :data:`typing.Union` [ :class:`.BridgeExtContext`, :class:`.BridgeApplicationContext` ] for typing convenience.
