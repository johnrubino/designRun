# Workspace topology

Agreed operating model for how designRun scales across products. **Model C: template-per-product.**

## Model C — template-per-product

- **Canonical studio:** [https://github.com/johnrubino/designRun](https://github.com/johnrubino/designRun) — the only source of truth for shared judgment. Improve `taste/`, `resources/`, `.agents/skills/`, `inspiration/`, and `patterns/` **here**.
- **Product repos:** each product is a **full clone/instance** created from this template (GitHub “Use this template” or equivalent). Not a thin pointer. Not a partial vendor of a few files.
- **Why:** designRun is built to be opened as the agent workspace root. Self-contained sessions need `taste/`, skills, `inspiration/`, and `projects/` as siblings.

```text
johnrubino/designRun          ← canonical studio (shared judgment lives here)
        │
        │  Use this template / full instance
        ▼
product-repo-A/               ← one product
product-repo-B/               ← one product
```

## Rules

1. **Shared layers are master-only in canonical.** Inside a product clone, treat `taste/`, `resources/`, `.agents/skills/`, and later promoted `patterns/` as **read-only as master**. Edit them only in the canonical repo, then sync forward into product instances.
2. **Product work stays in the product repo.** Product-specific work lives in `projects/<product>/` (brief, evidence, decisions, flows, prototypes, deliverables/specs) plus implementation in that same product repo (for example `app/` or an agreed code root).
3. **One active product per instance.** Do not stack unrelated products in one clone.
4. **Pattern promotion goes back to canonical.** When something proves reusable beyond one product, open a PR **back to canonical** — never only leave it in the product clone.
5. **Sync is intentional.** Pull shared paths from canonical into product instances on purpose (document the intent; a script can come later). Never silent drift by editing taste in the product as source of truth.
6. **Refuse these layouts:**
   - Putting implementation only in canonical
   - Forking canonical per product *without* treating canonical as the template source
   - Pointer-only / thin-studio layouts that leave the product harness without local taste and skills

## Roles

- **Donny (design):** works in the product instance; writes direction and specs under `projects/<product>/`; updates canonical taste only via PR when judgment changes globally.
- **Devi (engineering):** implements from project specs in the product repo; pushback on cost/feasibility updates decisions in that project.
- **John:** owns final taste; approvals land as rules in canonical taste when they are standing, not one-screen patches.

## Sync intent

Until a sync script exists:

1. Change shared judgment in [johnrubino/designRun](https://github.com/johnrubino/designRun).
2. Land it on canonical `main` through normal review.
3. Pull the shared paths (`taste/`, `resources/`, `.agents/skills/`, `inspiration/`, `patterns/` as applicable) forward into each product instance deliberately — not by rewriting taste inside the product as if it were master.

Product clones may diverge in `projects/` and implementation roots. Shared layers should not.
