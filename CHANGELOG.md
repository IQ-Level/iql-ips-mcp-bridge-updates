# Changelog

MCP Bridge – Custom Databases, for Invision Community 4.7 with Pages. Newest first.

| Version | Date | Changes |
| --- | --- | --- |
| 1.0.12 | 2026-11-19 | Update check: the ACP now shows when a new version is out (release channel IQ-Level/iql-ips-mcp-bridge-updates). Includes everything from 1.0.11: SEO fields (meta description, keywords, custom URL) for the AI and a separate image description for each uploaded photo. |
| 1.0.11 | 2026-11-12 | **SEO fields.** The meta description, keywords and custom URL of a record can be exposed to the AI per database, with instructions and length limits like other fields. The custom URL is checked like in the IPS form (unique, no clash with a Pages page) and the old address keeps redirecting. SEO values are kept in revisions, so a rollback restores them. **Image descriptions:** each uploaded photo can get its own alt text. |
| 1.0.10 | 2026-11-10 | **Edits without approval** as an option: per database, changes to published records are either proposals approved in the ACP or applied at once with a revision; a global setting can turn proposals off everywhere. **ACP notification** while proposals wait for review, cleared when they are approved or rejected. Clearer mode names. |
| 1.0.9 | 2026-11-10 | A full usage guide for the AI (workflow, images, rules) and clearer tool descriptions. The main image is also accepted inside the record fields; reading a record returns its main image. |
| 1.0.8 | 2026-11-10 | **Photos as files:** one-time signed upload links (valid 10 minutes, single use, up to 10 files), so the AI uploads photos attached to a chat without sending the access token. An uploaded image can be reused as the main image or in an Upload field. Main image on edits. |
| 1.0.7 | 2026-11-10 | **Images:** in the article body as native attachments, as the main image of the record with its thumbnail, and in image Upload fields. Search by status (published, waiting for approval, scheduled, hidden). |
| 1.0.6 | 2026-11-10 | First release: Pages databases over MCP with a field whitelist, access tokens with allowed authors, the native moderation queue for new records, proposals, revisions, log and rollback, relational fields (brand, shop) and field descriptions and limits taken from Pages. |
