# Security Policy

## Reporting a Vulnerability

This is a Claude Code skill. It runs in your Claude Code session and does not send your data to any WhyStrohm server.

If you discover a security concern (for example, the skill could be manipulated to execute unintended commands, or the scoring rules contain logic that could be exploited):

**Email:** hello@whystrohm.com

Please include:
- Description of the concern
- Steps to reproduce
- Potential impact

Do not open a public GitHub issue for security concerns.

## Scope

This skill has no backend, no database, and no authentication. It makes these network calls, all through Claude Code's own tools:

- **WebFetch** of the website URL you provide (homepage, and an about or services page).
- **WebFetch** of one public link to your recent content, only if you choose auto-pull in Step 4. This can be a blog index, a newsletter archive, a YouTube channel page, or a public YouTube feed.
- **WebSearch** to find a YouTube `channel_id`, only when you give a handle or channel URL and the feed needs the id.

Compliant sources only. The skill reads public pages and feeds. It never scrapes authenticated or walled platforms (LinkedIn, X/Twitter, Instagram) behind a login or with cookies. If a source is blocked, it asks you to paste instead.

The attack surface is the skill's markdown instructions, how Claude Code interprets them, and the content of the public pages it reads.
