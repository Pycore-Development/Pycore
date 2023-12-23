.. currentmodule:: pycore

Application Commands
====================


Command Permission Decorators
-----------------------------

.. autofunction:: pycore.commands.default_permissions
    :decorator:

.. autofunction:: pycore.commands.guild_only
    :decorator:

.. autofunction:: pycore.commands.is_nsfw
    :decorator:


Commands
--------

Shortcut Decorators
~~~~~~~~~~~~~~~~~~~

.. autofunction:: pycore.commands.application_command
    :decorator:

.. autofunction:: pycore.commands.command
    :decorator:

.. autofunction:: pycore.commands.slash_command
    :decorator:

.. autofunction:: pycore.commands.user_command
    :decorator:

.. autofunction:: pycore.commands.message_command
    :decorator:

Objects
~~~~~~~

.. attributetable:: ApplicationCommand
.. autoclass:: ApplicationCommand
    :members:

.. attributetable:: SlashCommand
.. autoclass:: SlashCommand
    :members:

.. attributetable:: SlashCommandGroup
.. autoclass:: SlashCommandGroup
    :members:

.. attributetable:: UserCommand
.. autoclass:: UserCommand
    :members:

.. attributetable:: MessageCommand
.. autoclass:: MessageCommand
    :members:

Options
-------

Shortcut Decorators
~~~~~~~~~~~~~~~~~~~
.. autofunction:: pycore.commands.option
    :decorator:

Objects
~~~~~~~

.. attributetable:: Option
.. autoclass:: Option
    :members:

.. attributetable:: ThreadOption
.. autoclass:: ThreadOption
    :members:

.. attributetable:: OptionChoice
.. autoclass:: OptionChoice
    :members:


Context Objects
---------------

.. attributetable:: ApplicationContext
.. autoclass:: ApplicationContext
    :members:

.. attributetable:: AutocompleteContext
.. autoclass:: AutocompleteContext
    :members:
