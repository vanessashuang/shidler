# AI Usage Prompt Log — FIN-321

**Student:** Vanessa Huang
**Course:** FIN-321, Spring 2026
**Assignment:** Stage 3 — Technical Specification
**LLM Used:** Claude Sonnet 4.6
**Date:** April 24, 2026

---

## Entry 1

**Prompt:**
> "Using the instructions for Stage 3 (Spec Assignment) and the template spec, create an extremely clear and conceptual deliverable for me. If details from my stage 2 deliverable is needed, use that too."

**Key Output:**
A complete `stage3-spec-Huang.md` file with all 8 required sections: Problem Statement, Inputs table (with all 10 named ranges, values, units, and sources), Assumptions & Constraints, Calculation Flow for all four hedge strategies, Outputs table, Model Review, Sensitivity Plan, and Limitations & Next Steps. All values were pulled directly from the Stage 2 Excel model (e.g., `FC_AMT` = €3,898,128.90, `USD_FORWARD` = $4,239,215, `USD_MM` = $4,571,691, put floor = $4,439,408, parity gap = $332,476).

**Disposition:** Used — accepted as the primary deliverable with one subsequent revision (see Entry 2).

---

## Entry 2

**Prompt:**
> "Double check to make sure it follows all the requirements for Stage 3 instructions."

**Key Output:**
A checklist review comparing the spec against every requirement in the Stage 3 assignment. All sections passed. One gap was identified: the Problem Statement lacked a quantified dollar figure for the business consequence of an adverse FX move. The AI patched the Problem Statement to add: "In the worst case of the modeled range (S_T = S₀ × 0.95 ≈ 1.0967), an unhedged position would yield approximately $4,275,000 — a shortfall of roughly $225,000 relative to the USD target."

**Disposition:** Used — the gap identified was valid and the correction was accepted. The updated file was used as the final deliverable.

---
