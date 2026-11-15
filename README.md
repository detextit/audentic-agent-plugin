# audentic Websites

Add an existing published [audentic](https://www.audentic.org) OpenAI voice agent to a React, Next.js, or HTML website with your coding assistant. The skill covers floating buttons, inline cards, exact website origins, typed input, microphone permissions, and mobile checks. audentic is an independent platform, not an OpenAI product.

## Install the skill

In your website repository, run the skills CLI and select your coding assistant:

```bash
npx skills add detextit/audentic-agent-plugin --skill audentic
```

Or download directly from audentic:

- [Standalone skill ZIP](https://www.audentic.org/downloads/audentic-skill.zip)
- [Portable plugin ZIP](https://www.audentic.org/downloads/audentic-website-plugin.zip)
- [Read SKILL.md](https://www.audentic.org/skills/audentic/SKILL.md)
- [Release version and SHA-256 checksums](https://www.audentic.org/downloads/manifest.json)

Extract the standalone skill so the final project path is `.agents/skills/audentic/SKILL.md` for local Codex or `.claude/skills/audentic/SKILL.md` for local Claude Code. Start a new session in the repository. Other hosts may have different discovery rules; see the [installation guide](https://www.audentic.org/docs/developers/coding-agents).

The plugin ZIP is an Agent Plugins package for compatible hosts; it is not a Claude plugin marketplace manifest. Direct downloads and this public repository do not imply an approved directory listing. The skill and plugin contain instructions, not the React widget itself.

## Give your assistant a task

> Use the audentic skill to add my published voice agent to this website. My agent ID is YOUR_AGENT_ID, my website is YOUR_WEBSITE_URL, and I want a floating button at bottom right. Use https://www.audentic.org as the audentic host. Inspect the existing integration, avoid duplicate widgets, run the normal checks, and tell me which exact website origins and live browser tests remain.

Replace the placeholders and describe your preferred placement. The assistant can edit your website when it has repository access, or provide snippets and setup steps in chat. No OpenAI key or account password is needed. The current examples match `@audentic/react` 0.7.0 and preserve an existing project's version unless a change is requested.

Create, review, test, and publish your agent in the [audentic workspace](https://www.audentic.org/agents/new). Set Starting language in About and approve each website origin in Test & publish. Follow the [OpenAI voice-agent guide](https://www.audentic.org/docs/build/openai-voice-agent) for the complete setup. The skill does not create or publish agents through private account endpoints, and no supported public management API or MCP server is currently available.

## What is included

- `skills/audentic/SKILL.md`: reusable website integration instructions.
- `plugin.json`: portable Agent Plugins metadata and OpenAI listing information.
- `assets/`: the referenced audentic brand icon.

There are no hooks, executable scripts, MCP servers, account connections, or installation dependencies in the package. No release license has been declared. The audentic name and logo identify the product; this repository does not grant trademark rights.

## Data and network behavior

The skill is instructions and does not itself execute code or connect to an audentic account on installation. Your assistant may read and edit website code, install the React package from npm, read public documentation, and run checks as part of your task. Its own processing and retention rules apply to material you give it.

After deployment, a visitor chooses to start a voice or typed conversation. The widget connects to audentic and the configured OpenAI voice service. Voice mode requests microphone permission; Type instead does not, but still uses a model connection and a conversation start. audentic saves text transcripts and supported visitor submissions. See the [Privacy Policy](https://www.audentic.org/privacy) for processing, retention, and deletion details.

## Help

Read the [coding-agent guide](https://www.audentic.org/docs/developers/coding-agents), [React guide](https://www.audentic.org/docs/developers/react), or [website widget guide](https://www.audentic.org/docs/deploy/website-widget). Report integration issues in this repository or contact Detextit at info.detextit@gmail.com.
