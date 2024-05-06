---
title: Lambda Expressions
---

# Lambda Expressions in Dawncord

Lambda expressions are a powerful feature of Java that allow for concise and expressive syntax when working with functional interfaces. In Dawncord, lambda expressions can be used to define event handlers and callbacks, making it easy to respond to various Discord events and interactions.

## Understanding Lambda Expressions

Lambda expressions in Java provide a way to define anonymous functions or "closures" inline, without the need for a separate method declaration. They are particularly useful for implementing functional interfaces, which define a single abstract method.

In Dawncord, lambda expressions are commonly used to define event handlers for handling Discord events such as slash commands, message components, and modals. They provide a clean and readable way to specify the behavior of your bot in response to specific events.

## Usage

Lambda expressions can be used in Dawncord to define event handlers for handling Discord events such as slash commands, message components, and modals.

### Example: Handling Slash Commands with Lambda Expressions

!!! example
    === "Creating role example"
        ```java
        // Handling slash command "role create" with a lambda expression
        bot.onSlashCommand("role create", event -> {
            // Create a role with a lambda expression
            event.getGuild().createRole(role -> {
                role.setName("Role Name");
                role.setColor(Color.BLACK);
            });
        });
        ```
    === "Creating modal example"
        ```java
        // Handling slash command "submit bag" with a lambda expression
        bot.onSlashCommand("submit bag", event -> {
            // Reply a modal with a lambda expression
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
    === "Handling modal example"
        ```java
        // Handling modal events with a lambda expression
        bot.onModal("modal", event -> {
            event.reply("Thanks for submitting!");
        });
        ```