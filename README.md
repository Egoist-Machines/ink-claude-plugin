# Ink

Deslop without losing the plot.

Ink is a writing tool that rewrites AI drafts and stiff, generic writing into words you would actually use, and keeps your meaning intact. This bundle connects assistants to Ink and adds a skill for rewriting pasted text or a local text or markdown file.

Use it on emails, cover letters, reports, product updates and posts. Ink runs its own rewriting model, then checks the result for the names, numbers, dates, quotes, citations and links you wrote, and warns you if one goes missing.

## What it includes

- **Ink MCP server** at `https://ink.ego.ist/mcp`, a remote server run by Egoist Machines, Inc. Its model-visible tools check your account (`ink_get_status`), start a rewrite (`ink_rewrite_text`), follow a queued job (`ink_get_job`, `ink_get_result`) and cancel one (`ink_cancel_job`). Two feedback tools are available only to the Ink widget.
- **Ink skill**, which uses MCP tools when available and the REST API otherwise. When you ask it to rewrite a local file, the assistant reads only that file and writes the rewrite to a new file beside it, such as `draft.ink.md`. It never overwrites the original or an existing file.

The plugin has no hooks, scripts, local servers or package installs.

## Install

The commands below use the public mirror. Version 0.1.2 must be synced there by the owner first. The directory listings are not submitted.

### Claude Code

```text
/plugin marketplace add Egoist-Machines/ink-claude-plugin
/plugin install ink@ink
```

Authenticate Ink through `/mcp`. [Claude Code marketplace instructions](https://code.claude.com/docs/en/discover-plugins).

### skills.sh

```sh
npx skills add Egoist-Machines/ink-claude-plugin --skill ink
```

Choose your agent in the installer. This installs the skill, not an MCP connection. If Ink MCP tools are unavailable, create a key at https://ink.ego.ist/app/api-keys and set `INK_API_KEY` in your local environment. Never paste it into chat. REST keys require a paid subscription; trials do not qualify, and unlimited accounts are exempt. [Skills CLI](https://skills.sh/docs), [API reference](https://ink.ego.ist/auth.md).

### Gemini CLI

```sh
gemini extensions install https://github.com/Egoist-Machines/ink-claude-plugin
```

Start Gemini and run `/mcp auth ink` to authorize in the browser. The extension uses HTTP MCP with automatic OAuth discovery. [Extension installation](https://geminicli.com/docs/extensions/reference/), [MCP authentication](https://geminicli.com/docs/tools/mcp-server/).

### Cursor

Until the plugin is reviewed and listed, install the skill with the skills.sh command above and choose Cursor. To use OAuth, add `{"mcpServers":{"ink":{"url":"https://ink.ego.ist/mcp"}}}` to `.cursor/mcp.json` and connect Ink in Cursor's MCP settings. Once listed, install Ink from Customize or the marketplace. [Cursor MCP](https://cursor.com/docs/mcp), [plugins](https://cursor.com/docs/plugins).

MCP sign-in uses OAuth on https://ink.ego.ist. Plans, trials and billing happen on the website. Then ask: "Rewrite this email with Ink" or "Rewrite notes.md with Ink".

## Data handling

- For rewriting, the assistant sends the text you supply and required arguments to Ink through `https://ink.ego.ist/mcp`, or `https://ink.ego.ist/api/v1/rewrites` for the REST fallback. For a local file, the skill tells the assistant to read only the file you name. Ink uses the service providers described in its Privacy Policy.
- Ink keeps rewrite text for 30 days, then deletes it. Your drafts and rewrites are not used for training unless you send feedback on them.
- Feedback is optional and only sent with the thumbs buttons in the Ink widget or on the website. It shares that rewrite's original and rewritten text and any note with Ink to improve its models, and that text is deleted after 90 days.

Details: [Privacy](https://ink.ego.ist/privacy), [Terms](https://ink.ego.ist/terms), [How agents connect](https://ink.ego.ist/agents).

## Status

Every rewrite uses the shared Ink model. Personal voice profiles are coming soon. PDF and DOCX rewriting is planned.

## Support

support@ego.ist

## License

The plugin files in this repository are MIT licensed. Use of the Ink service is governed by the [Ink terms](https://ink.ego.ist/terms).
