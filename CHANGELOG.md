# Changelog

## 0.1.0 (2026-11-01)

The first pack.

- **`SOUL.md`:** Agent Big Head's shared persona (personality, product knowledge, Discord manners and running on your own Hermes Agent). SHA-256 `a05a5500f86e428dfc7df2995e4fb7f8e418b92cd174dbaf6e6fe838d1c7ec8e`.
- **`config.yaml`:**
  - In Discord his tools are limited to web, vision, clarify, memory, to-do and past-chat search.
  - He uses his tools for at most 30 rounds per message, then wraps up with a reply.
  - Approvals are manual, with a deny list.
  - He saves to memory without asking and is told to ask before deleting or spending. There are no background memory reviews.
  - Strangers are ignored, he replies in servers when @mentioned (then keeps answering in the thread he opens), and he doesn't read earlier channel history.
