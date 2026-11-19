**MCP Bridge – Custom Databases** connects Invision Community 4.7 Pages databases to AI clients that speak MCP (Model Context Protocol), such as Claude. Editors decide which databases and fields the AI sees, and everything it writes goes through IPS's own moderation, revisions and permissions.

[Po polsku](README.pl.md) · [Changelog](CHANGELOG.md) · [iql.pl](https://iql.pl)

This repository is the public release channel: the current version and the changelog. The code and the application files are not here.

## Current version

| Application | Version | For |
| --- | --- | --- |
| MCP Bridge – Custom Databases | see [`latest.json`](latest.json) | Invision Community 4.7 with Pages |

IPS checks for new versions on its own: the application reads [`latest.json`](latest.json) in this repository and the ACP shows a "new version" badge next to it.

## What it does

An AI client connected to the forum can read records of the chosen Pages databases (articles, news, reviews) and write new ones or changes. It works through 11 MCP tools: list and describe databases, search and read records, find linked records (brands, shops), upload images, and create or update records.

| What the admin controls | How |
| --- | --- |
| Which databases the AI sees | ACP, per database; none by default |
| Which fields it reads and writes, and how to fill them | A whitelist of fields with instructions, examples and length limits. The field descriptions and limits set in Pages are used too. |
| SEO | Meta description, keywords and the custom URL of a record, switched on per database |
| Who the AI writes as | Access tokens created in the ACP: a default author and other allowed authors, the databases, read or write, expiry and IP addresses |
| What gets published | New records always wait in the native IPS moderation queue. Changes to published records are proposals approved in the ACP (with a notification), or are applied at once with a revision. |
| History | Every call is logged. Before each change a native Pages revision is stored, and a change can be rolled back with one click. |

## How it writes

- **Only through IPS's own models.** It runs no SQL on the database tables, so permissions, moderation, revisions, the search index, webhooks and forum topic sync work as for content added by hand.
- **Images as native forum files.** Images go in the article body as attachments, in the main image of the record and in Upload fields. The AI uploads files with a one-time signed link, so the access token never leaves the connector.
- **Relational fields** (brand, shop) are filled with records found in the linked databases; the linked databases stay read-only.
- **No deleting, approving, pinning or featuring.** The AI has no tool for those.

## Requirements

| | |
| --- | --- |
| Invision Community | 4.7 with Pages |
| PHP | 8.0–8.4 |
| MCP client | Claude.ai (custom connector), Claude Desktop, Claude Code or any client with Streamable HTTP |
