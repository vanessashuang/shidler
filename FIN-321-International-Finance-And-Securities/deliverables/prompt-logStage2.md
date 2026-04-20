# AI Prompt Log — FIN-321 Stage 2

**Student:** Vanessa H.
**Course:** FIN-321, Spring 2026
**Assignment:** Stage 2 — Excel Hedge Model Build
**AI Tool:** Claude Sonnet 4.6 (claude.ai)
**Date:** April 2026

---

## Prompt 1

**Prompt:**
> "I need you to build a completed Excel model for my finance class assignment. I'm attaching three things: (1) the assignment instructions, (2) the Excel skeleton template, and (3) my Stage 1 memo with all my scenario variables."

**Key Output:**
Initial Excel model (`Huang-Vanessa-stage2-model.xlsx`) with 6 sections: Inputs, Forward Hedge, Money Market Hedge, Option Hedges, Sensitivity Table (±5% in 1% steps with chart), and Summary Output. Named ranges defined for all key variables. Notes & Assumptions tab included.

**Status:** Modified
**Notes:** Accepted as a starting point but sent back for review. Several errors were identified in the next prompt.

---

## Prompt 2

**Prompt:**
> "Recheck it. Make sure it matches the data in the Stage 1 memo, follows the color coding convention, and that it honors the evaluation highlights."

**Key Output:**
Revised model fixing the following issues: (1) FC_AMT corrected from 3,898,854.61 to 3,898,128.90 EUR (wrong rounding in v1); (2) color coding updated to match assignment spec — added Blue assumption cells for FC_AMT derivation and CIP-implied forward, which were missing entirely in v1; (3) forward hedge result corrected to $4,239,215; (4) put floor corrected to $4,439,408; (5) named range formula errors (77 #VALUE! errors) fixed by replacing named ranges with absolute cell references for LibreOffice compatibility. 0 formula errors across 86 formulas.

**Status:** Modified
**Notes:** Numbers and color coding were accepted. Flagged the remaining issue of the $332K MM vs. Forward parity gap for a decision on how to handle it.

---

## Prompt 3

**Prompt:**
> "Well choose the path that best matches the instructions and would provide the best accuracy."

**Key Output:**
Amber callout box inserted on the main Hedge Model sheet directly below the parity check row, explaining that: (1) the MM steps correctly follow the textbook method and independently derive a CIP-implied forward of ~1.1728; (2) the scenario-provided F₀ = 1.0875 does not satisfy CIP with the given rates, producing a ~$332K gap; (3) this is a known scenario inconsistency, not a formula error. CIP deviation entry in Notes tab flagged in red as "KEY." Required multiple repair passes after row insertion broke downstream formula references (put floor, sensitivity table, summary output).

**Status:** Used
**Notes:** Accepted the AI's recommendation to keep the MM steps as correctly derived from interest rates and document the CIP deviation transparently, rather than forcing parity by overriding the forward rate.

---

## Prompt 4

**Prompt:**
> "I need to log all AI usage in a prompt log md file. For this conversation, record the prompt I used, the key output, and whether I used/modified/rejected it."

**Key Output:**
This file.

**Status:** Used

---

## Summary

| Prompt | Purpose | Status |
|--------|---------|--------|
| 1 | Build initial Excel model from memo + template | Modified |
| 2 | Audit and fix data, color coding, formula errors | Modified |
| 3 | Resolve MM vs. Forward parity gap with inline note | Used |
| 4 | Generate this AI usage log | Used |
