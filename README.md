# Agent Big Head for Hermes Agent

Agent Big Head is a quick, candid AI agent from IDuh Genius. This pack turns your own copy of Hermes Agent into Big Head and puts him in your own Discord. He runs on your computer, on the AI model you choose. Out of the box, he can talk, search the web and keep notes, but he can't run commands or touch your files.

Would you rather talk to a more buttoned-up agent? The [Genius pack](https://github.com/joshuajudd-usa/geniushq-hermes) gives you GeniusHQ instead, or you can run both as two separate bots.

**Early release (v0.1.1).** If something here doesn't work the way this page says, tell us. That's a bug, not you.

## What's in the pack

- **[`SOUL.md`](SOUL.md)**: who he is. That's his personality, his Discord manners and what he knows about IDuh Genius.
- **[`config.yaml`](config.yaml)**: careful starting settings:
  - In Discord his tools are web search, reading images, asking you a question, memory, a to-do list and searching his past chats. There's no terminal, files, code, browser, subagents or scheduled jobs.
  - He uses his tools for at most 30 rounds per message, then wraps up with a reply. That keeps one message from running on and on, but it isn't a spending limit.
  - He saves to memory without asking, and asks before deleting or spending.
  - He ignores strangers. In a server he answers when you @mention him, then keeps answering in the thread he opens.

There are no skills, plugins, scheduled jobs or keys in the pack. Read both files before you install, if you like.

## What you need

- A Mac with an Apple chip, a Linux computer or a Windows PC, switched on whenever you want him around
- Hermes Agent v0.22.5 or later
- A Discord account and a server where you have Manage Server
- An account with an AI model provider, which you pay directly, usually by usage
- About 30 minutes, and a terminal

## Set him up

1. **Install Hermes Agent.** Follow Nous Research's [installation guide](https://hermes-agent.nousresearch.com/docs/getting-started/installation).
2. **Add Big Head:**

   ```
   hermes profile install github.com/joshuajudd-usa/agent-big-head-hermes --alias
   ```

   This makes a Hermes profile named `bighead` and a `bighead` command. Hermes shows the pack's name, author and the settings it needs before it installs.
3. **Pick his model:**

   ```
   bighead model
   ```

   Choose a model with at least 64K of context.
4. **Create your Discord bot.**
   1. In the [Discord Developer Portal](https://discord.com/developers/applications), make a New Application.
   2. Open **Bot**, select **Reset Token** and copy the token. It's shown once.
   3. On the same page, turn on **Message Content Intent** and **Server Members Intent**.
   4. Turn **Public Bot** off, so only you can add him to servers.
5. **Connect Discord:**

   ```
   bighead gateway setup
   ```

   1. Choose Discord and paste the token.
   2. When it asks who may talk to him, give your own Discord user ID. To find it, turn on Developer Mode in Discord's **Settings → Advanced**, then right-click your name and choose **Copy User ID**.
   3. Add him to your server with this link, putting your application's ID in place of `APP_ID`. It asks only for the permissions he needs: reading and sending messages, threads, reactions, links and files.

      ```
      https://discord.com/oauth2/authorize?client_id=APP_ID&scope=bot+applications.commands&permissions=309237763136
      ```

      Never give him the Administrator permission.
6. **Start him:**

   ```
   bighead gateway
   ```

   To keep him running in the background, use `bighead gateway install` instead. On Windows with WSL2, Hermes says background services are unreliable, so use `bighead gateway run` in a terminal there.
7. **Say hello.** Send him a DM, or @mention him in your server. In a server he opens a thread and keeps answering there without another mention.

If your terminal can't find `bighead`, use `hermes -p bighead` in its place, for example `hermes -p bighead model`.

## Keep him safe

- **Allow only yourself.** Everyone on his allowed list can use every tool he has, and Hermes's docs don't say who may press an approval button, so assume anyone on the list can.
- **Keep him out of public servers.**
- **Memory is shared.** Whatever he saves can come back in any conversation, including in a server channel. He saves without asking, so don't tell him what you wouldn't want repeated in another channel. You can ask him what he remembers, and tell him to forget anything.
- **Your bot token and model API key are passwords.** They live in his profile's `.env` file and never in this repository. If one leaks, reset it at its source.
- **He asks before deleting or spending.** Hermes asks before commands it rates as risky, such as recursive deletes, if you turn on a terminal. His own rules also tell him to ask first, but that's an instruction, not a lock, and Hermes has no spending limit of its own.
- **Set a spending limit** with your model provider. Most providers bill by usage, so every message costs money there.
- **To stop him,** press Ctrl+C in the terminal where `bighead gateway` is running. If you installed him as a background service, Hermes's gateway guide shows how to stop it.

### If you give him more tools

`bighead tools` can switch on more tools in Discord, such as a terminal or files. Then he can run commands and change files on this computer. Before you do that:

- **Give him his own folder.** Make a folder for his work, and set `terminal.cwd` in `config.yaml` to its full path, so he doesn't start in your home folder.
- **Approvals only catch some things.** Hermes asks before commands it rates as risky, but not before every file change or every line of code he runs. Read what you approve.
- **Keep approvals yours alone.** Put only your own ID on his allowed list. Hermes's [Discord guide](https://hermes-agent.nousresearch.com/docs/user-guide/messaging/discord) doesn't describe a separate approver setting.
- **Use a sandbox.** For real isolation, run his commands inside Docker; see Hermes's [security guide](https://hermes-agent.nousresearch.com/docs/user-guide/security). The pack's deny list is a seatbelt, not a sandbox.

## What's ours and what isn't

- **Hermes Agent** is open-source software made by Nous Research. IDuh Genius isn't affiliated with Nous Research and doesn't control or support Hermes Agent.
- **Discord** is Discord's. Your bot is your own Discord application, and you're responsible for it under Discord's terms.
- **This pack** is ours. IDuh Genius doesn't run your Big Head and doesn't receive your conversations. Your messages go to Discord, to the model provider you chose, and to any service a tool uses (a web search provider, for example).

## Update or remove him

- **To update:** run `hermes profile update bighead`. This refreshes `SOUL.md`. Your `config.yaml`, `.env`, memories and chat history stay as they are. That means new safety settings in `config.yaml` don't arrive on their own. When a release changes them, the changelog says so, and `hermes profile update bighead --force-config` takes them; it replaces your `config.yaml`. Hermes can't pin a pack version yet, so an update always takes the latest.
- **To remove:** run `hermes profile delete bighead`. Hermes asks you to type his name to confirm, then permanently deletes his profile, including his memories, history and the keys saved in his `.env`. If you're done with your bot, delete it in the Discord Developer Portal too.

## Help

Contact us at [iduhgenius.com/contact](https://iduhgenius.com/contact/) or support@iduhgenius.com. For help with Hermes Agent itself, see Nous Research's [documentation](https://hermes-agent.nousresearch.com/docs/).

## License

See [LICENSE](LICENSE).

## Optional: IDuh Genius apps

Big Head can read and add to your Scatterplot inbox through the IDuh Genius MCP server. It is off by default. See [docs/iduh-mcp.md](docs/iduh-mcp.md).
