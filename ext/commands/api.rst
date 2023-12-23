.. currentmodule:: pycore

API Reference
=============

The following section outlines the API of pycore's prefixed command extension module.

.. note::

    Using prefixed commands in guilds requires :attr:`Intents.message_content` to be enabled.


.. _ext_commands_api_bot:

Bots
----

Bot
~~~

.. attributetable:: pycore.ext.commands.Bot

.. autoclass:: pycore.ext.commands.Bot
    :members:
    :inherited-members:
    :exclude-members: after_invoke, before_invoke, check, check_once, command, event, group, listen

    .. automethod:: Bot.after_invoke()
        :decorator:

    .. automethod:: Bot.before_invoke()
        :decorator:

    .. automethod:: Bot.check()
        :decorator:

    .. automethod:: Bot.check_once()
        :decorator:

    .. automethod:: Bot.command(*args, **kwargs)
        :decorator:

    .. automethod:: Bot.event()
        :decorator:

    .. automethod:: Bot.group(*args, **kwargs)
        :decorator:

    .. automethod:: Bot.listen(name=None, once=False)
        :decorator:

AutoShardedBot
~~~~~~~~~~~~~~

.. attributetable:: pycore.ext.commands.AutoShardedBot

.. autoclass:: pycore.ext.commands.AutoShardedBot
    :members:

Prefix Helpers
--------------

.. autofunction:: pycore.ext.commands.when_mentioned

.. autofunction:: pycore.ext.commands.when_mentioned_or

.. _ext_commands_api_events:

Event Reference
---------------

These events function similar to :ref:`the regular events <pycore-api-events>`, except they
are custom to the command extension module.

.. function:: pycore.ext.commands.on_command_error(ctx, error)

    An error handler that is called when an error is raised
    inside a command either through user input error, check
    failure, or an error in your own code.

    A default one is provided (:meth:`.Bot.on_command_error`).

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`
    :param error: The error that was raised.
    :type error: :class:`.CommandError` derived

.. function:: pycore.ext.commands.on_command(ctx)

    An event that is called when a command is found and is about to be invoked.

    This event is called regardless of whether the command itself succeeds via
    error or completes.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

.. function:: pycore.ext.commands.on_command_completion(ctx)

    An event that is called when a command has completed its invocation.

    This event is called only if the command succeeded, i.e. all checks have
    passed and the user input it correctly.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

.. _ext_commands_api_command:

Commands
--------

Decorators
~~~~~~~~~~

.. autofunction:: pycore.ext.commands.command
    :decorator:

.. autofunction:: pycore.ext.commands.group
    :decorator:

Command
~~~~~~~

.. attributetable:: pycore.ext.commands.Command

.. autoclass:: pycore.ext.commands.Command
    :members:
    :special-members: __call__
    :exclude-members: after_invoke, before_invoke, error

    .. automethod:: Command.after_invoke()
        :decorator:

    .. automethod:: Command.before_invoke()
        :decorator:

    .. automethod:: Command.error()
        :decorator:

Group
~~~~~

.. attributetable:: pycore.ext.commands.Group

.. autoclass:: pycore.ext.commands.Group
    :members:
    :inherited-members:
    :exclude-members: after_invoke, before_invoke, command, error, group

    .. automethod:: Group.after_invoke()
        :decorator:

    .. automethod:: Group.before_invoke()
        :decorator:

    .. automethod:: Group.command(*args, **kwargs)
        :decorator:

    .. automethod:: Group.error()
        :decorator:

    .. automethod:: Group.group(*args, **kwargs)
        :decorator:

GroupMixin
~~~~~~~~~~

.. attributetable:: pycore.ext.commands.GroupMixin

.. autoclass:: pycore.ext.commands.GroupMixin
    :members:
    :exclude-members: command, group

    .. automethod:: GroupMixin.command(*args, **kwargs)
        :decorator:

    .. automethod:: GroupMixin.group(*args, **kwargs)
        :decorator:

.. _ext_commands_api_cogs:

Cogs
----

Cog
~~~

.. attributetable:: pycore.ext.commands.Cog

.. autoclass:: pycore.ext.commands.Cog
    :members:

CogMeta
~~~~~~~

.. attributetable:: pycore.cog.CogMeta

.. autoclass:: pycore.cog.CogMeta
    :members:

.. _ext_commands_help_command:

Help Commands
-------------

HelpCommand
~~~~~~~~~~~

.. attributetable:: pycore.ext.commands.HelpCommand

.. autoclass:: pycore.ext.commands.HelpCommand
    :members:

DefaultHelpCommand
~~~~~~~~~~~~~~~~~~

.. attributetable:: pycore.ext.commands.DefaultHelpCommand

.. autoclass:: pycore.ext.commands.DefaultHelpCommand
    :members:
    :exclude-members: send_bot_help, send_cog_help, send_group_help, send_command_help, prepare_help_command

MinimalHelpCommand
~~~~~~~~~~~~~~~~~~

.. attributetable:: pycore.ext.commands.MinimalHelpCommand

.. autoclass:: pycore.ext.commands.MinimalHelpCommand
    :members:
    :exclude-members: send_bot_help, send_cog_help, send_group_help, send_command_help, prepare_help_command

Paginator
~~~~~~~~~

.. attributetable:: pycore.ext.commands.Paginator

.. autoclass:: pycore.ext.commands.Paginator
    :members:

Enums
-----

.. class:: BucketType
    :module: pycore.ext.commands

    Specifies a type of bucket for, e.g. a cooldown.

    .. attribute:: default

        The default bucket operates on a global basis.
    .. attribute:: user

        The user bucket operates on a per-user basis.
    .. attribute:: guild

        The guild bucket operates on a per-guild basis.
    .. attribute:: channel

        The channel bucket operates on a per-channel basis.
    .. attribute:: member

        The member bucket operates on a per-member basis.
    .. attribute:: category

        The category bucket operates on a per-category basis.
    .. attribute:: role

        The role bucket operates on a per-role basis.

        .. versionadded:: 1.3


.. _ext_commands_api_checks:

Checks
------

.. autofunction:: pycore.ext.commands.check(predicate)
    :decorator:

.. autofunction:: pycore.ext.commands.check_any(*checks)
    :decorator:

.. autofunction:: pycore.ext.commands.has_role(item)
    :decorator:

.. autofunction:: pycore.ext.commands.has_permissions(**perms)
    :decorator:

.. autofunction:: pycore.ext.commands.has_guild_permissions(**perms)
    :decorator:

.. autofunction:: pycore.ext.commands.has_any_role(*items)
    :decorator:

.. autofunction:: pycore.ext.commands.bot_has_role(item)
    :decorator:

.. autofunction:: pycore.ext.commands.bot_has_permissions(**perms)
    :decorator:

.. autofunction:: pycore.ext.commands.bot_has_guild_permissions(**perms)
    :decorator:

.. autofunction:: pycore.ext.commands.bot_has_any_role(*items)
    :decorator:

.. autofunction:: pycore.ext.commands.cooldown(rate, per, type=pycore.ext.commands.BucketType.default)
    :decorator:

.. autofunction:: pycore.ext.commands.dynamic_cooldown(cooldown, type=BucketType.default)
    :decorator:

.. autofunction:: pycore.ext.commands.max_concurrency(number, per=pycore.ext.commands.BucketType.default, *, wait=False)
    :decorator:

.. autofunction:: pycore.ext.commands.before_invoke(coro)
    :decorator:

.. autofunction:: pycore.ext.commands.after_invoke(coro)
    :decorator:

.. autofunction:: pycore.ext.commands.guild_only(,)
    :decorator:

.. autofunction:: pycore.ext.commands.dm_only(,)
    :decorator:

.. autofunction:: pycore.ext.commands.is_owner(,)
    :decorator:

.. autofunction:: pycore.ext.commands.is_nsfw(,)
    :decorator:

.. _ext_commands_api_context:

Cooldown
--------

.. attributetable:: pycore.ext.commands.Cooldown

.. autoclass:: pycore.ext.commands.Cooldown
    :members:

Context
-------

.. attributetable:: pycore.ext.commands.Context

.. autoclass:: pycore.ext.commands.Context
    :members:
    :inherited-members:
    :exclude-members: history, typing

    .. automethod:: pycore.ext.commands.Context.history
        :async-for:

    .. automethod:: pycore.ext.commands.Context.typing
        :async-with:

.. _ext_commands_api_converters:

Converters
----------

.. autoclass:: pycore.ext.commands.Converter
    :members:

.. autoclass:: pycore.ext.commands.ObjectConverter
    :members:

.. autoclass:: pycore.ext.commands.MemberConverter
    :members:

.. autoclass:: pycore.ext.commands.UserConverter
    :members:

.. autoclass:: pycore.ext.commands.MessageConverter
    :members:

.. autoclass:: pycore.ext.commands.PartialMessageConverter
    :members:

.. autoclass:: pycore.ext.commands.GuildChannelConverter
    :members:

.. autoclass:: pycore.ext.commands.TextChannelConverter
    :members:

.. autoclass:: pycore.ext.commands.VoiceChannelConverter
    :members:

.. autoclass:: pycore.ext.commands.StageChannelConverter
    :members:

.. autoclass:: pycore.ext.commands.CategoryChannelConverter
    :members:

.. autoclass:: pycore.ext.commands.ForumChannelConverter
    :members:

.. autoclass:: pycore.ext.commands.InviteConverter
    :members:

.. autoclass:: pycore.ext.commands.GuildConverter
    :members:

.. autoclass:: pycore.ext.commands.RoleConverter
    :members:

.. autoclass:: pycore.ext.commands.GameConverter
    :members:

.. autoclass:: pycore.ext.commands.ColourConverter
    :members:

.. autoclass:: pycore.ext.commands.EmojiConverter
    :members:

.. autoclass:: pycore.ext.commands.PartialEmojiConverter
    :members:

.. autoclass:: pycore.ext.commands.ThreadConverter
    :members:

.. autoclass:: pycore.ext.commands.GuildStickerConverter
    :members:

.. autoclass:: pycore.ext.commands.clean_content
    :members:

.. autoclass:: pycore.ext.commands.Greedy()

.. autofunction:: pycore.ext.commands.run_converters

Flag Converter
~~~~~~~~~~~~~~

.. autoclass:: pycore.ext.commands.FlagConverter
    :members:

.. autoclass:: pycore.ext.commands.Flag()
    :members:

.. autofunction:: pycore.ext.commands.flag

.. _ext_commands_api_errors:

Exceptions
----------

.. autoexception:: pycore.ext.commands.CommandError
    :members:

.. autoexception:: pycore.ext.commands.ConversionError
    :members:

.. autoexception:: pycore.ext.commands.MissingRequiredArgument
    :members:

.. autoexception:: pycore.ext.commands.ArgumentParsingError
    :members:

.. autoexception:: pycore.ext.commands.UnexpectedQuoteError
    :members:

.. autoexception:: pycore.ext.commands.InvalidEndOfQuotedStringError
    :members:

.. autoexception:: pycore.ext.commands.ExpectedClosingQuoteError
    :members:

.. autoexception:: pycore.ext.commands.BadArgument
    :members:

.. autoexception:: pycore.ext.commands.BadUnionArgument
    :members:

.. autoexception:: pycore.ext.commands.BadLiteralArgument
    :members:

.. autoexception:: pycore.ext.commands.PrivateMessageOnly
    :members:

.. autoexception:: pycore.ext.commands.NoPrivateMessage
    :members:

.. autoexception:: pycore.ext.commands.CheckFailure
    :members:

.. autoexception:: pycore.ext.commands.CheckAnyFailure
    :members:

.. autoexception:: pycore.ext.commands.CommandNotFound
    :members:

.. autoexception:: pycore.ext.commands.DisabledCommand
    :members:

.. autoexception:: pycore.ext.commands.CommandInvokeError
    :members:

.. autoexception:: pycore.ext.commands.TooManyArguments
    :members:

.. autoexception:: pycore.ext.commands.UserInputError
    :members:

.. autoexception:: pycore.ext.commands.CommandOnCooldown
    :members:

.. autoexception:: pycore.ext.commands.MaxConcurrencyReached
    :members:

.. autoexception:: pycore.ext.commands.NotOwner
    :members:

.. autoexception:: pycore.ext.commands.MessageNotFound
    :members:

.. autoexception:: pycore.ext.commands.MemberNotFound
    :members:

.. autoexception:: pycore.ext.commands.GuildNotFound
    :members:

.. autoexception:: pycore.ext.commands.UserNotFound
    :members:

.. autoexception:: pycore.ext.commands.ChannelNotFound
    :members:

.. autoexception:: pycore.ext.commands.ChannelNotReadable
    :members:

.. autoexception:: pycore.ext.commands.ThreadNotFound
    :members:

.. autoexception:: pycore.ext.commands.BadColourArgument
    :members:

.. autoexception:: pycore.ext.commands.RoleNotFound
    :members:

.. autoexception:: pycore.ext.commands.BadInviteArgument
    :members:

.. autoexception:: pycore.ext.commands.EmojiNotFound
    :members:

.. autoexception:: pycore.ext.commands.PartialEmojiConversionFailure
    :members:

.. autoexception:: pycore.ext.commands.GuildStickerNotFound
    :members:

.. autoexception:: pycore.ext.commands.BadBoolArgument
    :members:

.. autoexception:: pycore.ext.commands.MissingPermissions
    :members:

.. autoexception:: pycore.ext.commands.BotMissingPermissions
    :members:

.. autoexception:: pycore.ext.commands.MissingRole
    :members:

.. autoexception:: pycore.ext.commands.BotMissingRole
    :members:

.. autoexception:: pycore.ext.commands.MissingAnyRole
    :members:

.. autoexception:: pycore.ext.commands.BotMissingAnyRole
    :members:

.. autoexception:: pycore.ext.commands.NSFWChannelRequired
    :members:

.. autoexception:: pycore.ext.commands.FlagError
    :members:

.. autoexception:: pycore.ext.commands.BadFlagArgument
    :members:

.. autoexception:: pycore.ext.commands.MissingFlagArgument
    :members:

.. autoexception:: pycore.ext.commands.TooManyFlags
    :members:

.. autoexception:: pycore.ext.commands.MissingRequiredFlag
    :members:

.. autoexception:: pycore.ext.commands.CommandRegistrationError
    :members:


Exception Hierarchy
~~~~~~~~~~~~~~~~~~~

.. exception_hierarchy::

    - :exc:`~.pycoreException`
        - :exc:`~.commands.CommandError`
            - :exc:`~.commands.ConversionError`
            - :exc:`~.commands.UserInputError`
                - :exc:`~.commands.MissingRequiredArgument`
                - :exc:`~.commands.TooManyArguments`
                - :exc:`~.commands.BadArgument`
                    - :exc:`~.commands.MessageNotFound`
                    - :exc:`~.commands.MemberNotFound`
                    - :exc:`~.commands.GuildNotFound`
                    - :exc:`~.commands.UserNotFound`
                    - :exc:`~.commands.ChannelNotFound`
                    - :exc:`~.commands.ChannelNotReadable`
                    - :exc:`~.commands.BadColourArgument`
                    - :exc:`~.commands.RoleNotFound`
                    - :exc:`~.commands.BadInviteArgument`
                    - :exc:`~.commands.EmojiNotFound`
                    - :exc:`~.commands.GuildStickerNotFound`
                    - :exc:`~.commands.PartialEmojiConversionFailure`
                    - :exc:`~.commands.BadBoolArgument`
                    - :exc:`~.commands.ThreadNotFound`
                    - :exc:`~.commands.FlagError`
                        - :exc:`~.commands.BadFlagArgument`
                        - :exc:`~.commands.MissingFlagArgument`
                        - :exc:`~.commands.TooManyFlags`
                        - :exc:`~.commands.MissingRequiredFlag`
                - :exc:`~.commands.BadUnionArgument`
                - :exc:`~.commands.BadLiteralArgument`
                - :exc:`~.commands.ArgumentParsingError`
                    - :exc:`~.commands.UnexpectedQuoteError`
                    - :exc:`~.commands.InvalidEndOfQuotedStringError`
                    - :exc:`~.commands.ExpectedClosingQuoteError`
            - :exc:`~.commands.CommandNotFound`
            - :exc:`~.commands.CheckFailure`
                - :exc:`~.commands.CheckAnyFailure`
                - :exc:`~.commands.PrivateMessageOnly`
                - :exc:`~.commands.NoPrivateMessage`
                - :exc:`~.commands.NotOwner`
                - :exc:`~.commands.MissingPermissions`
                - :exc:`~.commands.BotMissingPermissions`
                - :exc:`~.commands.MissingRole`
                - :exc:`~.commands.BotMissingRole`
                - :exc:`~.commands.MissingAnyRole`
                - :exc:`~.commands.BotMissingAnyRole`
                - :exc:`~.commands.NSFWChannelRequired`
            - :exc:`~.commands.DisabledCommand`
            - :exc:`~.commands.CommandInvokeError`
            - :exc:`~.commands.CommandOnCooldown`
            - :exc:`~.commands.MaxConcurrencyReached`
    - :exc:`~.ClientException`
        - :exc:`~.commands.CommandRegistrationError`
