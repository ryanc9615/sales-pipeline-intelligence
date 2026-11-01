# Phase 07 — HTTP, JSON and API Fundamentals

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 07 — HTTP, JSON and API Fundamentals**, milestone **3 — HTTP fundamentals and shipped application**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Understand request/response transport and data contracts through a small local read-only exercise.

**Prerequisites:** Phase 06 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Create a small synthetic JSON records fixture equivalent to a known CSV fixture.
2. Serve only examples/api on localhost using Python http.server; explain method, host, port and path.
3. Fetch with urllib.request and an explicit timeout; inspect status, response headers and decoded JSON.
4. Observe and handle a missing-path 404; compare HTTP failure with a 200 response whose data fails business validation.
5. Use the shared validation and calculation semantics on decoded records; compare results to CSV and stop the server. Explain future authentication/pagination/rate-limit requirements without implementing them.

**Technical concepts:** HTTP GET, URLs, status codes, headers, JSON, timeout/error handling, transport versus schema validation.

**Commercial concepts:** CRM export versus integration, consistent snapshots, trustworthy inputs across transports.

**Acceptance evidence:**

- [ ] A real local GET response and 404 are observed and recorded.
- [ ] Equivalent JSON/CSV records yield the same validated calculation results.
- [ ] I can explain the transport/validation boundary and what a real CRM connector would still need.
- [ ] The exercise is local and optional at runtime; the dashboard works without it.

**Out of scope:** No public HTTP server, full REST backend, OAuth, real CRM requests, production integration or new application service.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Ask me to trace what happens between requesting a local JSON URL and obtaining a Python records list.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.
