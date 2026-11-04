# Ink

Deslop without losing the plot.

Ink is a writing tool that rewrites AI drafts and stiff, generic writing into words you would actually use, and keeps your meaning intact. This plugin connects Claude to Ink and adds a skill for rewriting pasted text or a local text or markdown file.

Use it on emails, cover letters, reports, product updates and posts. Ink runs its own rewriting model, then checks the result for the names, numbers, dates, quotes, citations and links you wrote, and warns you if one goes missing.

## What it includes

- **Ink MCP server** at `https://ink.ego.ist/mcp`, a remote server run by Egoist Machines, Inc. Its model-visible tools check your account (`ink_get_status`), start a rewrite (`ink_rewrite_text`), follow a queued job (`ink_get_job`, `ink_get_result`) and cancel one (`ink_cancel_job`). Two feedback tools are available only to the Ink widget.
- **Ink skill**, which tells Claude how to use those tools. When you ask it to rewrite a local file, Claude reads only that file and writes the rewrite to a new file beside it, such as `draft.ink.md`. It never overwrites the original or an existing file.

The plugin has no hooks, scripts, local servers or package installs.

## Install

In Claude, add Ink from the plugin directory. In Claude Code you can also run:

```
/plugin marketplace add Egoist-Machines/ink-claude-plugin
/plugin install ink@ink
```

The first time Claude calls Ink, you sign in on https://ink.ego.ist with OAuth. Plans, trials and billing are handled on the website, never in the conversation.

Then ask, for example: "Rewrite this email with Ink" or "Rewrite notes.md with Ink".

## Data handling

- For rewriting, Claude sends the text you supply and the required tool arguments to Ink at `https://ink.ego.ist/mcp`. For a local file, the skill tells Claude to read only the file you name. Ink uses the service providers described in its Privacy Policy.
- Ink keeps rewrite text for 30 days, then deletes it. Your drafts and rewrites are not used for training unless you send feedback on them.
- Feedback is optional and only sent with the thumbs buttons in the Ink widget or on the website. It shares that rewrite's original and rewritten text and any note with Ink to improve its models, and that text is deleted after 90 days.

Details: [Privacy](https://ink.ego.ist/privacy), [Terms](https://ink.ego.ist/terms), [How agents connect](https://ink.ego.ist/agents).

## Status

Every rewrite uses the shared Ink model. Personal voice profiles are coming soon. PDF and DOCX rewriting is planned.

## Support

support@ego.ist

## License

The plugin files in this repository are MIT licensed. Use of the Ink service is governed by the [Ink terms](https://ink.ego.ist/terms).
