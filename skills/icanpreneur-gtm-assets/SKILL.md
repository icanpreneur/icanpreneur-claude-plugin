---
name: icanpreneur-gtm-assets
description: 'Turn a Buyer Persona into go-to-market assets in Icanpreneur: a competitive assessment, positioning and messaging, a landing page, a sales deck, and a webpage or Google Slides preview. Use when the user wants a competitive assessment, positioning, messaging, landing-page copy, a sales or pitch deck, wants to edit or refine those, regenerate them, or get a preview link. Load `icanpreneur` first. Do not use for generic copywriting, building a custom website, or an unrelated presentation. Covers the generation order, which ID goes where, editing without regenerating, previews, and what the assets can and cannot claim.'
---

# Competitive assessment, positioning, landing page, sales deck and previews

Load [icanpreneur](../icanpreneur/SKILL.md) first; its rules apply.

```
Buyer Persona → Competitive assessment → Positioning and messaging → Landing page ─┐
                                                                  └→ Sales deck ──┴→ Preview (webpage / Google Slides)
```

- A competitive assessment needs a persona (`generate_competitive_assessment`, with `buyerPersonaId`). It compares the offering with the alternatives buyers could use, based on web research.
- Positioning needs a **competitive assessment** (`generate_positioning_and_messaging`, with `competitiveAssessmentDocumentId`). The persona comes from the assessment.
- A landing page or deck needs a **positioning document** (`generate_landing_page`, `generate_sales_deck`, with `positioningDocumentId`).
- A preview needs a landing page or deck (`generate_buyer_persona_document_preview`, with `buyerPersonaDocumentId`). Competitive assessments and positioning have no preview.

Done means the documents asked for are `ready` with `error: false`, requested previews are `ready` with `error: false` and a link, and the user knows what evidence the assets rest on. Generate only what was asked: "positioning" is not a request for a page and a deck. A request for positioning does include the competitive assessment it needs, unless a suitable one already exists.

## 1. Check the starting point

1. Find the workspace and persona. No persona → `icanpreneur-build-research`.
2. Competitive assessment generation requires `status: Complete` and a nonempty `description` (`get_buyer_persona`). This applies to existing personas too: Pending/Error is rejected even when fields from an older profile remain. Wait briefly or report the block; there is no tool to select a previous completed version. An empty Complete persona is not ready, and Complete does not prove recent interviews are included.
3. Count the real and synthetic interviews in the source research (`icanpreneur` → `references/evidence.md`). If mostly synthetic, say in the hand-over that the assets express a hypothesis. This is disclosure, not an approval step.
4. `list_buyer_persona_documents` shows what exists. Each generation makes a new document; if it is unclear whether to reuse an existing competitive assessment or positioning, ask.
5. Use the workspace or research language unless asked.

## 2. Generate

These calls are billable. Say which steps use credits, then run the chain the user asked for without stopping at each step.

1. Competitive assessment; wait for `ready: true` and `error: false` (`get_buyer_persona_document`; `text` can be null while saved content is unavailable). On `error: true`, report it. Never write the assessment, positioning, page or deck yourself in place of the generator.
2. Positioning from the assessment's `id`. Wait for `ready`. Pause to show the assessment first only if the user asked to review or refine it. Positioning captures the assessment when generated, so the time to change the assessment is before positioning is built.
3. Pause to show the positioning only if the user asked to review or refine it first. Otherwise continue. Pages and decks capture their source when generated, so the time to change the positioning is before they are built.
4. Landing page and/or deck from the positioning's `id`. Wait for `ready`.
5. A request for a preview is the authorization. Do not ask again because it is billable.

**Before editing any generated text, or generating or refreshing a preview, read [references/editing-and-previews.md](references/editing-and-previews.md).** Prefer editing the Markdown over regenerating.

## 3. Review after new evidence

When new interviews have changed the persona, or the user asks whether the assets still fit, compare before regenerating. Check the positioning against the persona on five points: core problem, desired outcomes, perceived barriers, decision criteria and customer language. Say where they differ. Regenerate positioning only if it no longer reflects the latest buyer understanding and the user asks. A Canvas or persona change alone does not show an asset must be regenerated. Regenerate pages and decks only after the positioning is settled.

Generated assets are strong first drafts, written with the customer as the hero and speaking to their problem, outcomes and reasons to act. Keep that structure when editing, and tell the user to refine them in their own voice and test them with target buyers.

## 4. Hand over

Report the documents (name, type, ready), preview links, the persona and evidence line, and any placeholders left. Offer to save the positioning decisions as a note. `export_buyer_persona` gives the persona as Markdown for a handover. Deleting: follow `icanpreneur` and the reference.

## Mistakes to avoid

- Regenerating to make a small change, or regenerating a deck preview repeatedly (each is a new presentation).
- Sending `text` for only part of a document.
- Adding proof points no tool returned.
- Pausing for approval at each billable step of a chain the user asked for.
