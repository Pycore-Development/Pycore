.. _pycore_ext_bridge:

pycore.ext.bridge
==================

.. versionadded:: 2.0

This module allows using one command callback in order to make both a prefix command and a slash command.
This page includes the API reference/documentation for the module, but only contains a short example. For a more
detailed guide on how to use this, see our `pycore.ext.bridge guide <https://guide.pycore.dev/extensions/bridge>`_.

Example usage:

.. code-block:: python3

    import pycore
    from pycore.ext import bridge

    intents = pycore.Intents.default()
    intents.message_content = True

    bot = bridge.Bot(command_prefix="!", intents=intents)

    @bot.bridge_command()
    async def hello(ctx):
        await ctx.respond("Hello!")

    @bot.bridge_command()
    async def bye(ctx):
        await ctx.respond("Bye!")

    @bot.bridge_command()
    async def sum(ctx, first: int, second: int):
        s = first + second
        await ctx.respond(f"{s}")

    bot.run("TOKEN")


.. toctree::
    :maxdepth: 2

    api
