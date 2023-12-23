.. _pycore_ext_pages:

pycore.ext.pages
=================

.. versionadded:: 2.0

This module provides an easy pagination system with buttons, page groups, and custom view support.

Example usage in a cog:

.. code-block:: python3

    import asyncio

    import pycore
    from pycore.commands import SlashCommandGroup
    from pycore.ext import commands, pages


    class PageTest(commands.Cog):
        def __init__(self, bot):
            self.bot = bot
            self.pages = [
                "Page 1",
                [
                    pycore.Embed(title="Page 2, Embed 1"),
                    pycore.Embed(title="Page 2, Embed 2"),
                ],
                "Page Three",
                pycore.Embed(title="Page Four"),
                pycore.Embed(title="Page Five"),
                [
                    pycore.Embed(title="Page Six, Embed 1"),
                    pycore.Embed(title="Page Seven, Embed 2"),
                ],
            ]
            self.pages[3].set_image(
                url="https://c.tenor.com/pPKOYQpTO8AAAAAM/monkey-developer.gif"
            )
            self.pages[4].add_field(
                name="Example Field", value="Example Value", inline=False
            )
            self.pages[4].add_field(
                name="Another Example Field", value="Another Example Value", inline=False
            )

            self.more_pages = [
                "Second Page One",
                pycore.Embed(title="Second Page Two"),
                pycore.Embed(title="Second Page Three"),
            ]

            self.even_more_pages = ["11111", "22222", "33333"]

        def get_pages(self):
            return self.pages

        pagetest = SlashCommandGroup("pagetest", "Commands for testing ext.pages")

        # These examples use a Slash Command Group in a cog for better organization - it's not required for using ext.pages.
        @pagetest.command(name="default")
        async def pagetest_default(self, ctx: pycore.ApplicationContext):
            """Demonstrates using the paginator with the default options."""
            paginator = pages.Paginator(pages=self.get_pages())
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="hidden")
        async def pagetest_hidden(self, ctx: pycore.ApplicationContext):
            """Demonstrates using the paginator with disabled buttons hidden."""
            paginator = pages.Paginator(pages=self.get_pages(), show_disabled=False)
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="loop")
        async def pagetest_loop(self, ctx: pycore.ApplicationContext):
            """Demonstrates using the loop_pages option."""
            paginator = pages.Paginator(pages=self.get_pages(), loop_pages=True)
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="strings")
        async def pagetest_strings(self, ctx: pycore.ApplicationContext):
            """Demonstrates passing a list of strings as pages."""
            paginator = pages.Paginator(
                pages=["Page 1", "Page 2", "Page 3"], loop_pages=True
            )
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="timeout")
        async def pagetest_timeout(self, ctx: pycore.ApplicationContext):
            """Demonstrates having the buttons be disabled when the paginator view times out."""
            paginator = pages.Paginator(
                pages=self.get_pages(), disable_on_timeout=True, timeout=30
            )
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="remove_buttons")
        async def pagetest_remove(self, ctx: pycore.ApplicationContext):
            """Demonstrates using the default buttons, but removing some of them."""
            paginator = pages.Paginator(pages=self.get_pages())
            paginator.remove_button("first")
            paginator.remove_button("last")
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="init")
        async def pagetest_init(self, ctx: pycore.ApplicationContext):
            """Demonstrates how to pass a list of custom buttons when creating the Paginator instance."""
            pagelist = [
                pages.PaginatorButton(
                    "first", label="<<-", style=pycore.ButtonStyle.green
                ),
                pages.PaginatorButton("prev", label="<-", style=pycore.ButtonStyle.green),
                pages.PaginatorButton(
                    "page_indicator", style=pycore.ButtonStyle.gray, disabled=True
                ),
                pages.PaginatorButton("next", label="->", style=pycore.ButtonStyle.green),
                pages.PaginatorButton("last", label="->>", style=pycore.ButtonStyle.green),
            ]
            paginator = pages.Paginator(
                pages=self.get_pages(),
                show_disabled=True,
                show_indicator=True,
                use_default_buttons=False,
                custom_buttons=pagelist,
                loop_pages=True,
            )
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="emoji_buttons")
        async def pagetest_emoji_buttons(self, ctx: pycore.ApplicationContext):
            """Demonstrates using emojis for the paginator buttons instead of labels."""
            page_buttons = [
                pages.PaginatorButton(
                    "first", emoji="⏪", style=pycore.ButtonStyle.green
                ),
                pages.PaginatorButton("prev", emoji="⬅", style=pycore.ButtonStyle.green),
                pages.PaginatorButton(
                    "page_indicator", style=pycore.ButtonStyle.gray, disabled=True
                ),
                pages.PaginatorButton("next", emoji="➡", style=pycore.ButtonStyle.green),
                pages.PaginatorButton("last", emoji="⏩", style=pycore.ButtonStyle.green),
            ]
            paginator = pages.Paginator(
                pages=self.get_pages(),
                show_disabled=True,
                show_indicator=True,
                use_default_buttons=False,
                custom_buttons=page_buttons,
                loop_pages=True,
            )
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="custom_buttons")
        async def pagetest_custom_buttons(self, ctx: pycore.ApplicationContext):
            """Demonstrates adding buttons to the paginator when the default buttons are not used."""
            paginator = pages.Paginator(
                pages=self.get_pages(),
                use_default_buttons=False,
                loop_pages=False,
                show_disabled=False,
            )
            paginator.add_button(
                pages.PaginatorButton(
                    "prev", label="<", style=pycore.ButtonStyle.green, loop_label="lst"
                )
            )
            paginator.add_button(
                pages.PaginatorButton(
                    "page_indicator", style=pycore.ButtonStyle.gray, disabled=True
                )
            )
            paginator.add_button(
                pages.PaginatorButton(
                    "next", style=pycore.ButtonStyle.green, loop_label="fst"
                )
            )
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="custom_view")
        async def pagetest_custom_view(self, ctx: pycore.ApplicationContext):
            """Demonstrates passing a custom view to the paginator."""
            view = pycore.ui.View()
            view.add_item(pycore.ui.Button(label="Test Button, Does Nothing", row=1))
            view.add_item(
                pycore.ui.Select(
                    placeholder="Test Select Menu, Does Nothing",
                    options=[
                        pycore.SelectOption(
                            label="Example Option",
                            value="Example Value",
                            description="This menu does nothing!",
                        )
                    ],
                )
            )
            paginator = pages.Paginator(pages=self.get_pages(), custom_view=view)
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="groups")
        async def pagetest_groups(self, ctx: pycore.ApplicationContext):
            """Demonstrates using page groups to switch between different sets of pages."""
            page_buttons = [
                pages.PaginatorButton(
                    "first", label="<<-", style=pycore.ButtonStyle.green
                ),
                pages.PaginatorButton("prev", label="<-", style=pycore.ButtonStyle.green),
                pages.PaginatorButton(
                    "page_indicator", style=pycore.ButtonStyle.gray, disabled=True
                ),
                pages.PaginatorButton("next", label="->", style=pycore.ButtonStyle.green),
                pages.PaginatorButton("last", label="->>", style=pycore.ButtonStyle.green),
            ]
            view = pycore.ui.View()
            view.add_item(pycore.ui.Button(label="Test Button, Does Nothing", row=2))
            view.add_item(
                pycore.ui.Select(
                    placeholder="Test Select Menu, Does Nothing",
                    options=[
                        pycore.SelectOption(
                            label="Example Option",
                            value="Example Value",
                            description="This menu does nothing!",
                        )
                    ],
                )
            )
            page_groups = [
                pages.PageGroup(
                    pages=self.get_pages(),
                    label="Main Page Group",
                    description="Main Pages for Main Things",
                ),
                pages.PageGroup(
                    pages=[
                        "Second Set of Pages, Page 1",
                        "Second Set of Pages, Page 2",
                        "Look, it's group 2, page 3!",
                    ],
                    label="Second Page Group",
                    description="Secondary Pages for Secondary Things",
                    custom_buttons=page_buttons,
                    use_default_buttons=False,
                    custom_view=view,
                ),
            ]
            paginator = pages.Paginator(pages=page_groups, show_menu=True)
            await paginator.respond(ctx.interaction, ephemeral=False)

        @pagetest.command(name="update")
        async def pagetest_update(self, ctx: pycore.ApplicationContext):
            """Demonstrates updating an existing paginator instance with different options."""
            paginator = pages.Paginator(pages=self.get_pages(), show_disabled=False)
            await paginator.respond(ctx.interaction)
            await asyncio.sleep(3)
            await paginator.update(show_disabled=True, show_indicator=False)

        @pagetest.command(name="target")
        async def pagetest_target(self, ctx: pycore.ApplicationContext):
            """Demonstrates sending the paginator to a different target than where it was invoked."""
            paginator = pages.Paginator(pages=self.get_pages())
            await paginator.respond(ctx.interaction, target=ctx.interaction.user)

        @commands.command()
        async def pagetest_prefix(self, ctx: commands.Context):
            """Demonstrates using the paginator with a prefix-based command."""
            paginator = pages.Paginator(pages=self.get_pages(), use_default_buttons=False)
            paginator.add_button(
                pages.PaginatorButton("prev", label="<", style=pycore.ButtonStyle.green)
            )
            paginator.add_button(
                pages.PaginatorButton(
                    "page_indicator", style=pycore.ButtonStyle.gray, disabled=True
                )
            )
            paginator.add_button(
                pages.PaginatorButton("next", style=pycore.ButtonStyle.green)
            )
            await paginator.send(ctx)

        @commands.command()
        async def pagetest_target(self, ctx: commands.Context):
            """Demonstrates sending the paginator to a different target than where it was invoked (prefix-command version)."""
            paginator = pages.Paginator(pages=self.get_pages())
            await paginator.send(ctx, target=ctx.author, target_message="Paginator sent!")


    def setup(bot):
        bot.add_cog(PageTest(bot))

.. _pycore_ext_pages_api:

API Reference
-------------

Page
~~~~

.. attributetable:: pycore.ext.pages.Page

.. autoclass:: pycore.ext.pages.Page
    :members:

Paginator
~~~~~~~~~

.. attributetable:: pycore.ext.pages.Paginator

.. autoclass:: pycore.ext.pages.Paginator
    :members:
    :inherited-members:

PaginatorButton
~~~~~~~~~~~~~~~

.. attributetable:: pycore.ext.pages.PaginatorButton

.. autoclass:: pycore.ext.pages.PaginatorButton
    :members:
    :inherited-members:

PaginatorMenu
~~~~~~~~~~~~~

.. attributetable:: pycore.ext.pages.PaginatorMenu

.. autoclass:: pycore.ext.pages.PaginatorMenu
    :members:
    :inherited-members:

PageGroup
~~~~~~~~~

.. attributetable:: pycore.ext.pages.PageGroup

.. autoclass:: pycore.ext.pages.PageGroup
    :members:
    :inherited-members:
