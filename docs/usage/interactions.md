---
title: Interactions
---

# Interactions

In Dawncord, you can interact with Discord through various means, including slash commands, message components, and modals. This guide will show you how to handle each type of interaction.

## Slash Command Interaction

Slash commands allow users to interact with your bot by typing a command prefixed with a forward slash (/) in Discord.

### Registering Slash Commands

To register a slash command, you can use the registerSlashCommands method of the Dawncord class. Here's how you can register a slash command named "ping":

!!! example
    ```java
    // Register slash command "ping"
    SlashCommand command = new SlashCommandBuilder("ping", "Ping").build();
    bot.registerSlashCommands(command);
    ```

### Using Slash Commands

To use slash commands in your Discord bot, you can follow this example code snippet:

!!! example
    === "Checking command name"
        ```java
        // Handling slash command events and checking command name
        bot.onSlashCommand(event -> {
            if (event.getCommandName().equals("test")) {
                event.reply(event.getGuild().getName());
            }
        });
        ```
    === "Without checking command name"
        ```java
        // Registering a specific slash command without checking command name
        bot.onSlashCommand("test", event -> {
            event.reply(event.getGuild().getName());
        });
        ```

In the first example, the bot checks the command name inside the onSlashCommand event handler. In the second example, the command name is directly provided in the onSlashCommand method, so the bot doesn't need to check it inside the event handler.

### Handling Slash Command options

Here are two examples how to handle Slash command options in your Discord bot:

!!! example
    === "Using a builder"
        ```java
        // Creating a slash command with an option using a builder
        SlashCommand command = new SlashCommandBuilder("user", "User")
                .addOption(OptionType.USER, "info", "User info")
                .build()
        ```

    === "Separately"
        ```java
        // Define an option for the slash command
        Option option = new Option(OptionType.USER, "info", "User info")

        // Create a slash command with the defined option
        SlashCommand command = new SlashCommandBuilder("user", "User")
                .addOption(option)
                .build();
        ```

Handling options
!!! example
    ```java
    //Handling option
    bot.onSlashCommand("user", event -> {
        event.reply(event.getOption("info").getAsMention());
    });
    ```

### Subcommands

Subcommands in Discord's slash commands allow you to organize related functionalities under a single parent command, streamlining command structure and enhancing user experience.

To use subcommands in your Discord bot, you can follow this example code snippet:
!!! example
    ```java
    // Creating a slash command with a subcommand
    SlashCommand command = new SlashCommandBuilder("user", "User")
            .addSubCommand(new SubCommandBuilder("info", "Info").build())
            .addSubCommand(new SubCommandBuilder("ban", "Ban").build())
            .build();
    ```

### Subcommand Groups

Subcommand groups in Discord's slash commands allow you to organize related subcommands under a common category. They provide a hierarchical structure for your commands, enhancing organization and clarity.

To use subcommand groups in your Discord bot, you can follow this example code snippet:
!!! example
    ```java
    SlashCommand command = new SlashCommandBuilder("user", "User")
            .addSubCommandGroup(
                new SubCommandGroupBuilder("list", "List")
                    .addSubCommand(
                        new SubCommandBuilder("offline", "List offline users").build())
                    .addSubCommand(
                        new SubCommandBuilder("online", "List online users").build())
                    .build())
            .build();
    ```

## Message Component Interaction

Message components allow users to interact with messages by clicking buttons, selecting options from dropdown menus, etc.

### Button Component

Button components allow users to trigger actions by clicking on buttons embedded within messages.

To use button interactions in your Discord bot, you can follow this example code snippet:
!!! example
    ```java
    bot.onSlashCommand("button", event -> {
        event.reply(message -> {
            message.setComponents(
                Component.actionRow(
                    Button.primary("button", "Button")
                )
            );
        });
    });

    bot.onButton("button", event -> {
        event.reply("Button pressed");
    });
    ```

### Select Menu Component

Select menu components, also known as dropdown menus, allow users to choose from a list of options presented in a dropdown menu format.

To use select menu interactions in your Discord bot, you can follow this example code snippet:
!!! example
    ```java
    bot.onSlashCommand("selectmenu", event -> {
        event.reply(message -> {
            message.setComponents(
                Component.actionRow(
                    SelectMenu.create(SelectMenuType.USER, "user-select")
                )
            );
        });
    });

    bot.onSelectMenu("user-select", event -> {
        event.reply("Selected: " + event.getValues().asMembers().get(0).getUser().getUsername());
    });
    ```

## Modal Interaction

Modal components allow users to interact with your bot through dialog boxes or pop-up modals, enabling more complex interactions.

To create modal, you can follow this example code snippet:

!!! example
    === "Using builder"
        ```java
        bot.onSlashCommand("modal", event -> {
            Modal modal = new ModalBuilder("Submit bag", "submit-bag",
                List.of(
                    new Element("Title", "title", TextInputStyle.SHORT),
                    new Element("Operating system", "os", TextInputStyle.SHORT),
                    new Element("Browser", "browser", TextInputStyle.SHORT),
                    new Element("Details", "details", TextInputStyle.PARAGRAPH)
                ))
                .build();   

            event.replyModal(modal);
        });
        ```
    === "Using lambda"
        ```java
        bot.onSlashCommand("modal", event -> {
            event.replyModal(modal -> {
                modal.setTitle("Submit Bag");
                modal.setCustomId("submit-bag");
                modal.setElements(
                    new Element("Title", "title", TextInputStyle.SHORT),
                    new Element("Operating system", "os", TextInputStyle.SHORT),
                    new Element("Browser", "browser", TextInputStyle.SHORT),
                    new Element("Details", "details", TextInputStyle.PARAGRAPH)
                );
            });
        });
        ```

Respond to modal
!!! example
    ```java
    bot.onModal("submit-bag", event -> {
        event.getModal().getElements().stream().map(e -> e.getCustomId() + ": " + e.getValue()).forEach(System.out::println);   

        event.reply("Thanks for submitting!");
    });
    ```