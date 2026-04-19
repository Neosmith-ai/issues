# NeoSmith — Issues & Feedback

Welcome. This is the **public issue tracker** for everyone using NeoSmith —
the router that sits between your coding agents (Claude Code, Cursor,
Lovable) and the model backends.

> 🔓 **This repo is public.** Issues, comments, and code references here are
> visible to anyone on the internet — including other NeoSmith customers. Use
> the guidance below to decide what belongs here vs. a private channel.

---

## Where to report what

| Kind of thing | Best channel |
|---|---|
| 🐛 **General bug** (reproducible, not tied to private data) | **Open an issue here** |
| 💡 **Feature request / idea** | **Open an issue here** |
| ❓ **"How do I…" question** | **Open an issue here** or [Discussions](../../discussions) |
| 📚 **Docs typo or unclear section** | **Open an issue here** |
| 🚨 **Production outage** affecting your team | Your **private chat channel** with NeoSmith (Slack/Teams/Google Chat) — don't wait on public tickets |
| 🔐 **Security vulnerability** | Email `security@neosmith.ai` (PGP key on the website). **Do not** post here. |
| 💳 **Billing / contract / cap adjustment** | Ask your NeoSmith account owner privately |
| 🧪 **Customer-confidential reproducer** (paste of your prompts, request IDs tied to your org) | Your private chat channel, not here |

If you're unsure — start in your private chat channel. We'll move it here if
it's safe to discuss publicly.

---

## Opening an issue

Click **[New issue](../../issues/new/choose)** and pick the template that fits:

- **🐛 Bug report** — something that was working isn't, or returned an unexpected response
- **💡 Feature request** — a capability you want us to add
- **❓ Question / docs** — "how do I X?" or "the docs say X but actually Y"

### What to include

1. **The symptom** in one sentence
2. **Client + version** (Claude Code / Cursor / Lovable / other)
3. **Timestamp and approximate region** (UTC ± 10 min)
4. **Minimal reproducer** that doesn't contain your proprietary prompts

### What NOT to include

- **API keys** — if you ever paste one, rotate it immediately via your admin
- **Customer names / internal project names** if they're confidential
- **Full prompt bodies** — if the issue depends on the exact prompt, share a
  redacted version or send the **request ID** (from response header
  `X-NeoSmith-Request-ID`) via your private chat channel — we can fetch the
  trace server-side without it being in public view

---

## Self-serve first

Before opening a ticket, these often resolve the issue faster:

```bash
# Check your own key works
curl -s https://router.neosmith.ai/whoami \
  -H "Authorization: Bearer $ANTHROPIC_API_KEY"

# See your usage + remaining tokens
curl -s https://router.neosmith.ai/me.json \
  -H "Authorization: Bearer $ANTHROPIC_API_KEY"

# Live service status
curl -s https://router.neosmith.ai/status | grep -E 'Operational|Degraded'
```

| Problem | Quickest fix |
|---|---|
| `401 Unknown API key` | Key typo or revoked — ask your admin to re-mint |
| `429 dev_hard_ceiling_reached` | You hit your admin-configured hard cap — ask them to raise it |
| Request routed to wrong model | Force Opus with `[opus]` at the start of the message |
| Per-repo usage isn't attributing | Send header `X-NeoSmith-Project: org/repo` on requests |
| Response missing `X-NeoSmith-*` headers | Check ALB didn't strip them; confirm with direct `curl` |

---

## How fast will you respond?

| Priority | Response target |
|---|---|
| P1 (broad outage, security) | **Use your private channel, not here** |
| Bug (this repo) | < 1 business day to triage, assign, label |
| Feature request | < 2 business days to accept/decline with reasoning |
| Question | < 1 business day |

Every issue gets a NeoSmith owner within the response target. Labels you'll
see: `triage · bug · feature · docs · help-wanted · wontfix · duplicate`.

---

## Discussions vs issues

Use **[Discussions](../../discussions)** for:
- Asking a general "how do I" question that might help others
- Sharing a cool integration pattern
- Product feedback that's not yet a concrete feature request

Use **issues** for concrete, actionable things with a definition of "done".

---

## Contributing to docs

We welcome PRs to fix docs typos and clarify steps. For bigger doc
restructures, open an issue first to align on scope.

---

## License

Issues + discussions in this repo are public under the MIT license. Any
code samples we post in comments are public-domain / MIT.

---

*NeoSmith AI · Public issue tracker · For private support, use your
customer chat channel · contact-us@neosmith.ai*
