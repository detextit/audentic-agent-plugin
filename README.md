# audentic Websites

Install an existing published [audentic](https://www.audentic.org) voice agent on a website using a reusable agent skill. It supplies React and HTML integration patterns, explains exact website origins, and helps diagnose publication, microphone, iframe, and Content Security Policy issues.

In an environment with website repository access, the skill adapts the integration to the project and runs its normal checks. In chat, it returns code and setup instructions. Supply your agent ID and, for a custom deployment, your audentic application origin. Create, test, publish, and configure the agent's allowed websites in the audentic workspace.

## What's included

The package contains one skill, portable Agent Plugins metadata, a Claude plugin manifest, and the audentic icon. It has no MCP server, hooks, executable scripts, installation dependencies, or account connection. Installing the plugin does not create an agent or change an audentic account. It does not offer subscriptions or checkout.

## Use it

Ask to add a published audentic agent to a React website, generate its HTML embed, or diagnose a widget connection problem. Give the assistant the agent ID, target website origin, and relevant code or error. Agent IDs are public widget identifiers; no OpenAI key or account password is needed.

You can also give a coding assistant the [hosted skill](https://www.audentic.org/skills/audentic/SKILL.md). Marketplace publication and acceptance are separate from this source package.

Install the standalone skill into a supported coding agent using the skills CLI:

```bash
npx skills add detextit/audentic-agent-plugin --skill audentic
```

The [public source repository](https://github.com/detextit/audentic-agent-plugin) contains only this integration package. Public directory review, approval, and indexing are tracked separately; this repository does not imply an approved ChatGPT or Claude directory listing.

## Data and network behavior

The skill itself stores no data and runs no code on installation. Your assistant may read website code, edit it, install the published `@audentic/react` package from npm, read audentic's public documentation, and run checks when those actions are part of your task. No repository files or chat transcript are sent to audentic by the skill. Your assistant provider's own processing and retention rules apply to the material you give it.

After you deploy and a visitor chooses to start a voice conversation, the generated widget connects to your audentic deployment and OpenAI over WebRTC. audentic saves text transcripts and supported visitor submissions; the platform does not store audio recordings. Saved transcripts have no automatic expiry in the current application. This is behavior of the deployed widget, not of installing or invoking this skill. See the [Privacy Policy](https://www.audentic.org/privacy) for providers, retention, and deletion options. The browser asks the visitor for microphone permission.

## Support and license

Read the [React guide](https://www.audentic.org/docs/developers/react) and [coding-agent guide](https://www.audentic.org/docs/developers/coding-agents), or contact Detextit at info.detextit@gmail.com. License approval and directory submissions are pending. The audentic name and logo identify the product; no trademark rights are granted.
