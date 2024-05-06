---
title: Initialize your bot
---

# Using Dawncord

This guide will show you how to use Dawncord in your Java Discord bot projects.

## Adding Dawncord to Your Project

Before you can start using Dawncord, you need to add it as a dependency to your Java project. You can do this using either Maven or Gradle, as explained in the [Installation Guide](../installation.md).

## Creating a Discord Bot

To create a Discord bot using Dawncord, follow these steps:

### Initialize Your Bot

Create a new Java class for your bot and define the main method:

```java
public static void main(String[] args) {
    Dawncord bot = new Dawncord("YOUR_BOT_TOKEN");
    bot.setIntents(GatewayIntent.MESSAGE_CONTENT, GatewayIntent.GUILD_MEMBERS);
    bot.start();
}
```

Replace "YOUR_BOT_TOKEN" with your actual Discord bot token obtained from the Discord Developer Portal.