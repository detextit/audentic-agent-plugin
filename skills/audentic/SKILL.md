---
name: audentic
description: Install or troubleshoot an existing audentic website voice agent using the React component, floating voice button, or HTML embed. Use for audentic widget integration, allowed-origin failures, and microphone or iframe setup. Agent creation and publication happen in the audentic workspace.
---

# Install an audentic website voice agent

Add an agent the owner has configured in audentic to the requested website. Use this skill when someone asks to add audentic, embed their audentic agent, or fix its website integration. For creating an agent, send the owner to the [quickstart](https://www.audentic.org/docs/quickstart) and [workspace](https://www.audentic.org/agents/new); a gallery fork is also a private draft that needs review and publication.

## Establish the integration

- Get the agent ID from the user, project, or owner-generated **Test & publish** snippet. Never invent an ID. The ID can appear in website code; it is not an account credential.
- Default the audentic application origin to `https://www.audentic.org`. Preserve another deployment supplied by the owner. The website origin and audentic origin are different inputs.
- Inspect the site's framework, package manager, existing widget placement, and deployment URL. Follow its conventions and keep the change limited to the requested integration.
- Use React for a React app. Use the hosted floating button or inline embed for a site builder or HTML website. Preserve the owner's requested placement and avoid adding a second widget where one already exists.
- With no repository access, provide the matching snippet and owner setup steps in chat. Say which values to replace and which checks remain; do not claim files were edited or a build passed.

The examples below match `@audentic/react` 0.6.1. If the project already pins another release, inspect its API and current [React guide](https://www.audentic.org/docs/developers/react) before changing that dependency.

## React and Next.js

For a new installation, use the project's package manager; the npm form is:

```bash
npm install @audentic/react@0.6.1
```

The package supports React 18.2 and React 19 and includes its own styles. Render `SessionControl` with the real agent ID. In a Next.js App Router app, put it in a Client Component and import that component into the desired page or layout:

```tsx
"use client";

import { SessionControl } from "@audentic/react";

export function VoiceAssistant() {
  return <SessionControl agentId="YOUR_AGENT_ID" showTranscript />;
}
```

The default API URL is `https://www.audentic.org/api`. For another audentic deployment, set `apiBaseUrl="https://YOUR_AUDENTIC_DOMAIN/api"`, including `/api`. Optional `widgetConfiguration` changes presentation. The owner controls the voice, instructions, business knowledge, tools, and conversation duration in audentic.

## HTML or a website builder

Prefer the snippet generated in the agent's **Test & publish** panel. A floating button needs this script once in the site's custom code area:

```html
<script
  src="https://www.audentic.org/widget.js"
  data-agent-id="YOUR_AGENT_ID"
  data-position="bottom-right"
  defer
></script>
```

`data-position` accepts `bottom-right`, `bottom-left`, `top-right`, and `top-left`. For a voice card inside a page section, use:

```html
<script src="https://www.audentic.org/embed.js" defer></script>
<audentic-embed
  agent-id="YOUR_AGENT_ID"
  api-base-url="https://www.audentic.org/api"
  show-transcript
></audentic-embed>
```

For another audentic deployment, replace the script host and inline API host together. The floating button derives its API URL from the script host. Its panel opens before the visitor chooses to start the microphone.

## Owner setup and verification

In **Test & publish**, the owner must save and test the agent, add each website's exact origin to **Website addresses**, and select **Publish agent** for a draft or **Save & update live agent** for a published agent. `https://example.com` and `https://www.example.com` are separate origins; staging needs its own entry. Use no paths or wildcards. Local HTTP is supported for localhost with the actual port, such as `http://localhost:4000`. A draft can be integrated now, but visitors cannot connect until publication.

Run the site's usual build or typecheck when repository access is available. Then test the published website while signed out of audentic: load the widget, start a real microphone conversation, hear a reply, interrupt, and end the call. Confirm that the microphone indicator turns off. A successful builder preview or build does not verify the external site's origin, audio, or iframe permissions. Report the exact origins to add and distinguish checks performed from checks left for the owner.

## Diagnose a failing widget

| Symptom | Check and next action |
| --- | --- |
| Widget absent | Confirm the script or React component is rendered, the agent ID is real, and the site builder permits scripts on the published page. Check the network and console for loading errors. |
| Agent unavailable or website rejected | Verify the ID, publication status, saved settings, and exact page origin, including hostname and local port. Ask the owner to update **Website addresses**. |
| No microphone or audio | Use HTTPS or localhost, grant browser microphone permission, and check the selected input device and WebRTC support. Test in a normal browser tab. |
| Embedded page fails | The containing iframe needs `allow="microphone; autoplay"`. Site-builder preview restrictions can differ from the published page. |
| CSP blocks loading or interaction | Check actual violations. Permit the audentic scripts, API host in `connect-src`, audentic host in `frame-src` for custom interactive views, and the widget's inline styles within the site's existing CSP approach. |
| Rate limit or provider error | Read the returned status and message. Respect the retry delay; persistent errors need the owner's audentic/provider configuration review. |

Keep OpenAI keys, Clerk secrets, and account credentials out of website code and chat. Visitor session tokens and browser Origin headers do not authorize account management. Do not call private account endpoints to create, edit, or publish agents. Installing a widget does not add booking, payment, email delivery, or other business actions; describe only the agent's configured capabilities.

Use the [website widget guide](https://www.audentic.org/docs/deploy/website-widget), [React guide](https://www.audentic.org/docs/developers/react), and [coding-agent guide](https://www.audentic.org/docs/developers/coding-agents) for current integration details. The [gallery](https://www.audentic.org/gallery) offers public examples; those agents are approved for the gallery's own origin, so the owner should fork and configure an agent for their website.
