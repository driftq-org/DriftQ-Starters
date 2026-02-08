# DriftQ-Starters 🚀

Starter templates for DriftQ — **copy/paste production patterns** for durable, replayable workflows.

These are intentionally small repos you can use as a baseline when you’re building real systems that need:
- retries + backoff
- DLQ (dead-letter queue)
- replay
- safe side effects (idempotency)

---

## Templates

### 1) driftq-starter-fastapi-nextjs — “DLQ → Replay → Success” in ~2 minutes
**FastAPI API + Next.js UI + worker**, wired to DriftQ-Core (Docker Compose).

This is the “show it, don’t explain it” demo:
- force a failure
- watch retries
- DLQ payload persists
- replay with a fix applied → success ✅
- UI streams the run timeline live via **SSE**

**Repo:** https://github.com/driftq-org/driftq-starter-fastapi-nextjs
**Best for:** quick demos, onboarding, proving the DLQ/replay story

---

### 2) driftq-side-effects-starter — idempotency + safe retries (no duplicate side effects)
A more **production-ish** starter that proves a real claim:

> Retries won’t duplicate side effects — even if the worker crashes mid-step and DriftQ redelivers the message.

It shows a clean pattern:
- DriftQ for durable commands + redelivery
- idempotent worker
- **exactly-once markers** stored in SQLite (`effect_id`)
- simple proof artifacts you can eyeball

**Repo:** https://github.com/driftq-org/driftq-side-effects-starter
**Best for:** payments/webhooks/tickets/LLM tool calls where double-execution is unacceptable

---

## DriftQ-Core (the engine)
These starters are just templates. The engine lives here:

https://github.com/driftq-org/DriftQ-Core
