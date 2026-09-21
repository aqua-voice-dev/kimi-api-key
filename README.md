# Kimi API Key

*Unofficial community guide for the Kimi API. Not affiliated with Moonshot AI or Kimi. All trademarks belong to their owners.*

A kimi api key is the credential you create in the Kimi API Platform console at platform.kimi.ai to call the Kimi models - K3, the K2.7 code model, K2.6 - from your own code or from the tools the platform documents integrations for (Kimi Code CLI, Codex, Claude Code, OpenCode, OpenClaw, Hermes Agent). This guide covers where the key lives, how to create and store it, where the pricing is documented, and the mistakes that cost people their first afternoon.

> Need image, video or audio models rather than a chat model? [Try Synexa - one REST endpoint and Python SDK for FLUX, video and audio models](https://synexa.ai?utm_source=github&utm_medium=ugc&utm_campaign=kimi-api-key&utm_content=readme-top&utm_term=tier-r) is an alternative worth trying; it bills per run.

## What it is

The Kimi API Platform (its own tagline: Kimi LLM Open Platform, build with Kimi API) is the developer side of Kimi. Its documentation is organised as Guides, an API Reference, and Models and Pricing, with a User Center at platform.kimi.ai/console/account and a Playground for trying requests without code. API keys are managed at platform.kimi.ai/console/api-keys; that page requires a login, so it is not reproduced here, but it is the one page every other step depends on.

The models behind the key are listed on the Model List page. At the time of writing the platform is promoting Kimi K3, described as its most capable flagship model with a 1M-token context, alongside the Kimi K2.7 code model and Kimi K2.6, each with its own quickstart. Capabilities documented as guides include thinking models, reasoning effort, multi-turn chat, streaming, JSON mode, partial mode, vision input, context caching, dynamic tool loading, tool calls, web search (built-in and best-practice guides), official tools, tool choice, a response_format guide, automatic reconnection, file-based Q and A, and a Batch API.

## How to get a key

1. Open platform.kimi.ai and use Login in the top navigation, or Get Started, which goes to the console.
2. Open the User Center (platform.kimi.ai/console/account) to confirm the account and organisation you are creating the key under. The docs have a best-practices page for organisation management; read it if more than one person will use the account.
3. Go to API Keys at platform.kimi.ai/console/api-keys and create a key. Copy it and store it somewhere safe immediately.
4. Put it in an environment variable rather than in code: `export KIMI_API_KEY=...` in your shell, or a .env file that is in .gitignore.
5. Test it in the Playground (platform.kimi.ai/playground) before writing any code, so you know a failure later is your code and not the key.
6. Read the Quickstart and the Model List, pick a model ID from the list, and only then open the API Reference for the request shape.

## Pricing and limits

Pricing lives on the Models and Pricing page (platform.kimi.ai/docs/pricing/chat). The platform also links a separate Kimi Business plan page on kimi.com and a Contact Sales form. None of the numbers are reproduced here because they change; check the pricing page for current rates and any free allowance before budgeting.

## Practical notes and gotchas

- **Never commit the key.** Read it from the environment in every language. Add .env to .gitignore before the first commit, not after.
- **One key per project or tool.** If you use the key in Claude Code, Codex and a script, give each its own key so you can revoke one without breaking the others. The organisation management guide is the place to set that up.
- **Use the Playground and the debugging tool.** The docs include a Playground page and a guide to an API debugging tool (moonpalace). Reproduce a failing request there before assuming the API is at fault.
- **The docs publish an llms.txt index** at platform.kimi.ai/docs/llms.txt. If you are pointing an agent at the docs, feed it that file first rather than crawling.
- **Long jobs and bulk jobs have their own guides.** Automatic reconnection covers dropped streams; the Batch API guide covers bulk work. Do not hand-roll either.
- **Model IDs come from the Model List page.** The marketing names (K3, K2.7 Code, K2.6) are not necessarily the identifiers the API expects; copy the exact string from the list.

## Comparison

| | Kimi API | OpenRouter | Synexa |
|---|---|---|---|
| Where the key comes from | platform.kimi.ai/console/api-keys | An OpenRouter account (listed among the platform's partners; details not in the sources) | A Synexa account |
| Models | Kimi K3, K2.7 Code, K2.6 and others on the Model List | Not stated in the sources | FLUX, video and audio models |
| Modalities documented | Text chat, vision input, tool calls, web search, file-based Q and A, batch | Not stated in the sources | Image, video, audio |
| Billing | See the Models and Pricing page | Not stated in the sources | Pay per run |
| Client | REST API plus documented integrations (Kimi Code CLI, Codex, Claude Code, OpenCode) | Not stated in the sources | One REST endpoint plus a Python SDK |

## FAQ

**Where do I find my kimi api key?**
In the console at platform.kimi.ai/console/api-keys, after logging in. The User Center at platform.kimi.ai/console/account is the account-level page next to it.

**Can I use the key with Claude Code, Codex or OpenCode?**
The docs have an integration guide for each of those, plus Kimi Code CLI, OpenClaw and Hermes Agent. Follow the specific guide; the setup differs per tool.

**Which model should I start with?**
The platform currently promotes Kimi K3 as its flagship with a 1M-token context and has a dedicated K3 quickstart. If your task is code, there is a separate K2.7 code model quickstart. Check the Model List for the exact IDs.

**Is there a free tier?**
The pages this guide is based on do not state one. The Models and Pricing page is the authority; check it rather than relying on a forum answer.

**Can I get Kimi models through OpenRouter instead?**
OpenRouter appears among the partners on the platform's home page, but the sources do not describe that route. If you already have an OpenRouter key, check its model catalogue directly.

## Closing thoughts

A Kimi API key is quick to create and the docs around it are thorough: quickstarts per model, a Playground, a debugging tool, integration guides for the common coding agents. If your project also needs to generate images, video or audio from code, that is not what this key is for. [Try Synexa - one REST endpoint and Python SDK for FLUX, video and audio models](https://synexa.ai?utm_source=github&utm_medium=ugc&utm_campaign=kimi-api-key&utm_content=readme-top&utm_term=tier-r) covers that side with per-run billing, and the two sit comfortably next to each other in the same .env file.
