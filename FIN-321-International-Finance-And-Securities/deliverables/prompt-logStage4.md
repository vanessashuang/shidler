# AI Use Log — FIN-321 FX Hedge Analysis Project
**Student:** Vanessa Huang
**Course:** FIN-321, Spring 2026
**LLM Used:** Claude Sonnet 4.6 (claude.ai)
**Stages Covered:** Stage 3 (Specification) and Stage 4 (Final Analysis & Prompt)

---

## Entry 1 — Stage 3 Technical Specification

**Date:** April 24, 2026

**Prompt used:**
> Uploaded Stage 2 Excel model (`Huang-Vanessa-stage2-model.xlsx`). Asked Claude to generate a formal technical specification documenting the model's analytical structure, formula logic, key assumptions, and proposed improvements — formatted as a professional `.md` file for a treasury analyst or AI model-builder audience.

**Key output:**
A complete `Stage3-spec-Huang.md` file including: problem statement, inputs table with named ranges, assumptions and constraints, step-by-step calculation flow for all four hedge strategies, outputs table, model review (what worked / what to improve), sensitivity plan, and limitations/next steps. All variable names (`FC_AMT`, `S0_in`, `F0_in`, `R_USD`, `R_FC`, `K_PUT`, `PREM_PUT`, etc.) and numeric results were drawn directly from the Stage 2 model.

**Disposition:** **Used with modifications.** Reviewed all formula descriptions and numeric values against the Stage 2 spreadsheet for accuracy. Added judgment on the CIP deviation framing (the spec correctly flags it as a scenario inconsistency rather than a formula error — this characterization was verified and retained). Minor edits made to prose flow and the "What to Improve" table to reflect my own analytical priorities.

---

## Entry 2 — Stage 4 Initial Draft

**Date:** April 28, 2026

**Prompt used:**
> Uploaded `Huang-Vanessa-stage2-model.xlsx`, `Stage3-spec-Huang.md`, and `stage4-final-analysis-assignment.md`. Asked Claude to produce the complete Stage 4 deliverable following the assignment instructions: exposure summary (A), hedge outcome summary (B), sensitivity interpretation (C), strategic recommendation (D), executive justification (E), and structured AI prompt (F), plus extra credit sections.

**Key output:**
A full `Huang-Vanessa-stage4-final-analysis.md` file covering all six required sections. Key analytical outputs: recommended EUR put option hedge with $4,439,408 floor; forward hedge result of $4,239,215; money market result of $4,571,691 with CIP deviation documented; breakeven S_T of ~$1.1388; structured AI prompt with named ranges, color-coding spec, formula logic, and verification checks. Two extra credit sections on AI automation and multi-file reasoning/GitHub.

**Disposition:** **Used as draft, then revised in Entry 3.** The structure and coverage were strong, but specific numerical claims and the extra credit section count required verification and correction before submission.

---

## Entry 3 — Stage 4 Double-Check and Refinement

**Date:** April 28, 2026

**Prompt used:**
> "Double check and refine it" — asked Claude to audit the Stage 4 draft against the Stage 2 Excel model and Stage 3 specification for numerical accuracy, internal consistency, logical correctness, and assignment completeness.

**Key output:**
Claude ran a Python verification script recomputing all key figures from first principles, then identified and corrected the following:

| Issue | Original | Corrected |
|---|---|---|
| Breakeven S_T | ~$1.1388 | ~$1.1389 (formula: K_PUT − FV_PREM_PUT/FC_AMT) |
| Breakeven % description | "~1.4% below spot" | "~1.35% below spot" (consistent with premium % in Section E) |
| AI prompt — depreciation summary label | "Forward / Put Floor" | "MM Hedge / Forward Lock" (matching model's actual depreciation ranking) |
| AI prompt — verification checks | 5 checks; breakeven missing | Added CHECK 5: breakeven S_T formula (called out in Stage 3 spec as a required improvement) |
| Extra credit coverage | 2 of 3 topics | Added third section: Accounting & Audit Integration (ASC 815/IFRS 9, OCI treatment, GitHub as hedge documentation) |

**Disposition:** **Used with review.** All five corrections were verified independently before accepting. The breakeven formula and CIP parity logic were re-checked by hand. The added accounting section reflects my own understanding of ASC 815 hedge accounting requirements from course materials.

---

## Summary

| Entry | Stage | Role of AI | Disposition |
|---|---|---|---|
| 1 | Stage 3 | Generated specification draft from Excel model | Used with modifications |
| 2 | Stage 4 | Generated full memo draft from spec + Excel + assignment | Used as draft, revised |
| 3 | Stage 4 | Audited and corrected numerical and logical errors | Used with review |

**Overall assessment:** AI assistance materially accelerated drafting and formatting. All quantitative outputs were verified against the Stage 2 spreadsheet. Analytical judgments — particularly the CIP deviation characterization, the recommendation rationale, and the hedge accounting commentary — were reviewed and confirmed to reflect my own understanding of the material before submission.

---

*Log prepared by: Vanessa Huang | April 28, 2026*
