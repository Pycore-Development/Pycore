.. _pycore_api_abcs:

Abstract Base Classes
=====================

An :term:`abstract base class` (also known as an ``abc``) is a class that models can inherit
to get their behaviour. **Abstract base classes should not be instantiated**.
They are mainly there for usage with :func:`isinstance` and :func:`issubclass`\.

This library has a module related to abstract base classes, in which all the ABCs are subclasses of
:class:`typing.Protocol`.

.. attributetable:: pycore.abc.Snowflake

.. autoclass:: pycore.abc.Snowflake()
    :members:

.. attributetable:: pycore.abc.User

.. autoclass:: pycore.abc.User()
    :members:

.. attributetable:: pycore.abc.PrivateChannel

.. autoclass:: pycore.abc.PrivateChannel()
    :members:

.. attributetable:: pycore.abc.GuildChannel

.. autoclass:: pycore.abc.GuildChannel()
    :members:

.. attributetable:: pycore.abc.Messageable

.. autoclass:: pycore.abc.Messageable()
    :members:
    :exclude-members: history, typing

    .. automethod:: pycore.abc.Messageable.history
        :async-for:

    .. automethod:: pycore.abc.Messageable.typing
        :async-with:

.. attributetable:: pycore.abc.Connectable

.. autoclass:: pycore.abc.Connectable()
