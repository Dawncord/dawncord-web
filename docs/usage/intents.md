---
title: Gateway Intents
---

# Gateway Intents in Dawncord

Gateway intents are a fundamental concept in Discord bot development, allowing bots to subscribe to specific types of events from Discord servers. In Dawncord, gateway intents are represented by the `GatewayIntent` enum, which provides a set of predefined intents that can be used to control the types of events your bot receives.

## Understanding Gateway Intents

Gateway intents define the types of events that your bot will receive from Discord servers. By subscribing to specific intents, you can control which events your bot is notified of, enabling more efficient event handling and reducing unnecessary traffic.

## Available Gateway Intents

The `GatewayIntent` enum provides a set of predefined intents that you can use to specify the types of events your bot is interested in. Here are some of the available gateway intents in Dawncord:

- `GUILDS`: Allows access to guilds.
- `GUILD_MEMBERS`: Allows access to guild members.
- `GUILD_MESSAGES`: Allows access to guild messages.
- `GUILD_MESSAGE_REACTIONS`: Allows access to reactions on guild messages.
- `DIRECT_MESSAGES`: Allows access to direct messages.
- `DIRECT_MESSAGE_REACTIONS`: Allows access to reactions on direct messages.
- And more...

For a complete list of available gateway intents and their descriptions, refer to the `GatewayIntent` enum in the Dawncord documentation or Javadocs.

## Usage

To specify which gateway intents your bot should subscribe to, you can use the `setIntents()` method provided by the `Dawncord` class. For example:

!!! example
    ```java
    public class MyDiscordBot {
        public static void main(String[] args) {
            Dawncord bot = new Dawncord("TOKEN");
            
            // Subscribe to GUILD_MESSAGES and MESSAGE_CONTENT intents
            bot.setIntents(GatewayIntent.GUILD_MESSAGES, GatewayIntent.MESSAGE_CONTENT);
            
            bot.start();
        }
    }
    ```
