# FX Hedge Analysis — Executive Memo & Strategy Recommendation
**FIN-321 Stage 4 | Analyst: Vanessa Huang | Date: April 28, 2026**
**Audience: CFO / Director of Treasury**

---

## A. Exposure Summary

A U.S.-based solar equipment importer holds a EUR-denominated receivable of **€3,898,129** (equivalent to **$4,500,000 USD** at inception) due in 12 months, with a settlement date of approximately April 2, 2027. The receivable was booked on April 2, 2026 at a spot rate of **$1.1544/EUR**.

The core FX risk is straightforward: if the EUR depreciates against the USD before settlement, the firm will receive fewer dollars than anticipated when converting the EUR proceeds. In the most adverse scenario modeled (S_T = $1.0967, a 5% EUR decline), unhedged USD receipts fall to approximately **$4,275,000** — a **$225,000 shortfall** relative to the $4,500,000 target. This magnitude of loss is material relative to typical corporate treasury budgets and justifies a deliberate hedging decision.

The business context adds urgency: as a solar equipment importer, the firm likely operates on thin margins tied to USD-denominated project costs, financing obligations, and domestic pricing commitments. A $225,000 FX loss is not a rounding error — it can meaningfully erode project-level returns or force repricing. The hedging decision is not speculative; it is a cash-flow protection exercise.

---

## B. Summary of Hedge Outcomes

The Stage 2 model evaluated four strategies across an 11-point sensitivity range (S_T from $1.0967 to $1.2121). Key results are summarized below.

| Strategy | Locked/Floor USD Proceeds | Key Characteristic |
|---|---|---|
| **Forward Hedge** | $4,239,215 (fixed) | Eliminates all FX risk; no upside participation |
| **Money Market Hedge** | $4,571,691 (fixed) | Synthetic forward; higher than F₀-based result due to CIP deviation |
| **Put Option (ATM, K = $1.1544)** | $4,439,408 (floor) | Floor + upside participation; net of $60,592 FV premium cost |
| **Call Option** | N/A (reference only) | Applies to payables, not this receivable |
| **No Hedge** | $4,275,000–$4,725,000 | Full EUR/USD exposure; highest risk and highest theoretical upside |

**Forward Hedge:** At $4,239,215, the forward locks in a definitive USD amount that is actually below the $4,500,000 target — a consequence of the scenario-provided forward rate ($1.0875/EUR) sitting well below both the inception spot and the CIP-implied rate. The forward eliminates uncertainty but surrenders all appreciation upside and crystallizes a known shortfall relative to budget.

**Money Market Hedge:** The three-step borrow-convert-invest sequence produces $4,571,691 — $332,476 above the forward result. This divergence is not an error; it reflects the scenario's embedded CIP violation (the provided F₀ of $1.0875 does not satisfy covered interest parity given R_USD = 3.625% and R_FC = 2.00%, which imply a CIP forward of $1.1728). The money market result is mathematically correct and internally consistent, but requires the firm to carry a EUR-denominated borrowing on its balance sheet for 12 months, introducing liquidity and counterparty complexity.

**Put Option:** With a strike set at-the-money ($1.1544/EUR) and a premium of $0.015/EUR ($58,472 upfront, or $60,592 at maturity on a future-value basis), the put hedge establishes a floor of $4,439,408 — approximately $200,000 above the forward result — while preserving full upside if EUR strengthens. The breakeven spot rate (where put and no-hedge produce equal proceeds) is approximately $1.1389/EUR — computed as K_PUT − FV(PREM_PUT)/FC_AMT — meaning the insurance cost is recouped whenever EUR falls more than ~1.35% from spot.

**No Hedge:** Proceeds are entirely a function of S_T. At the midpoint (S_T = $1.1544), the firm receives exactly $4,500,000. At S_T = $1.2121, unhedged proceeds reach $4,725,000. The no-hedge baseline is the only strategy that can meet or exceed the $4,500,000 USD target — but it requires EUR to remain at or above spot, which is not guaranteed.

---

## C. Sensitivity Interpretation

The sensitivity table reveals meaningfully different risk profiles across the ±5% range.

**EUR Depreciation Scenarios (S_T < $1.1544):**

The forward hedge and money market hedge are flat-line protections — their proceeds are identical regardless of how far EUR falls. The put option also activates its floor at $4,439,408, providing better absolute protection than the forward. The unhedged position deteriorates linearly, reaching $4,275,000 at S_T = $1.0967. In depreciation environments, the ranking by USD proceeds is: MM Hedge > Put Floor > Forward > No Hedge. However, the MM hedge's superiority here is primarily an artifact of the CIP inconsistency in scenario inputs, not a generalizable conclusion.

**EUR Appreciation Scenarios (S_T > $1.1544):**

This is where the strategies diverge most sharply. Both the forward and money market hedges remain fixed — the firm earns no benefit from EUR strength. The put option, however, follows the market upward (minus the premium cost), producing proceeds of $4,484,408 at S_T = $1.1659, rising to $4,664,408 at S_T = $1.2121. The unhedged position captures the full gain. The forward hedge's opportunity cost in appreciation scenarios is the difference between $4,239,215 and what the firm would have received unhedged — a gap that reaches $485,785 at the top of the range.

**Key Trade-Off:** Certainty vs. optionality. The forward provides maximum certainty but forfeits all upside; the put provides a meaningful floor while preserving upside at the cost of a known premium. For a firm with strong balance sheet flexibility and a positive macro view on EUR, the put hedge delivers the most favorable risk-adjusted profile.

---

## D. Strategic Recommendation

**Recommended Strategy: EUR Put Option Hedge**

Based on the model outputs, the put option hedge is the most strategically sound choice for this receivable.

The floor of **$4,439,408** is $200,193 above the forward result and only $60,592 below the $4,500,000 USD target — a gap that represents the cost of insurance, not a structural shortfall. More importantly, the put preserves full participation in EUR appreciation above the $1.1544 strike. If EUR moves to $1.18 or higher — a plausible scenario given ECB policy normalization trends and U.S. dollar weakness signals in Q1 2026 — the firm captures incremental USD proceeds that would be foreclosed under the forward.

The put hedge also outperforms the forward in depreciation scenarios, because K_PUT ($1.1544) exceeds F₀ ($1.0875), meaning the floor is higher than the forward lock-in. This is an unusual configuration that specifically advantages the put in this scenario: the firm gets better downside protection *and* upside optionality, at the cost of a $60,592 premium.

The money market hedge produces the highest locked-in result ($4,571,691), but this figure is unreliable as a decision benchmark given the CIP deviation. A real-world money market hedge would produce proceeds consistent with covered interest parity — approximately $4,239,215, matching the forward — making the MM hedge effectively equivalent to the forward in an efficient market.

**Conclusion:** Recommend executing an at-the-money EUR put on €3,898,129 notional with a one-year tenor, paying a $58,472 upfront premium. This establishes a $4,439,408 USD floor while preserving upside participation if EUR/USD recovers toward or above spot.

---

## E. Executive Justification

**Cash Flow Stability:** The put hedge guarantees that USD receipts will not fall below $4,439,408 under any market scenario. This converts a variable, rate-sensitive cash inflow into a bounded outcome, enabling reliable project-level budgeting.

**Budget Certainty:** The $60,592 premium FV is a known, fixed cost that can be budgeted precisely at inception. This is categorically preferable to the open-ended downside of the no-hedge position, which could produce a $225,000 shortfall in adverse markets.

**Liquidity Impact:** Unlike the money market hedge, the put option does not require borrowing in EUR or carrying a foreign-currency liability. The only cash outflow is the premium, paid upfront. This avoids balance sheet complexity and preserves the firm's credit capacity for operational financing.

**Optionality Value:** In a rising-EUR environment, the put allows the firm to benefit fully from EUR/USD appreciation — something neither the forward nor the money market hedge permits. For a firm that believes EUR may strengthen (supported by ECB's relatively stable policy and continued U.S. fiscal uncertainty), this asymmetric payoff is valuable.

**Premium Costs:** At $0.015/EUR on an ATM strike with a one-year tenor, the put premium is reasonable. The total cost of $60,592 (FV) represents approximately 1.35% of the expected USD receivable — a cost comparable to FX bid-ask spreads and execution costs that would be incurred regardless of strategy. Management should view this as a hedging expense analogous to property insurance: not expected to be "profitable," but essential for risk management.

**Accounting Implications (Optional):** Under ASC 815 (IFRS 9), the put can be designated as a cash flow hedge of the EUR receivable, with changes in fair value recorded through Other Comprehensive Income (OCI) rather than P&L, subject to effectiveness testing. This avoids earnings volatility that would arise from marking the unhedged receivable to market each quarter. Proper hedge accounting documentation (risk management objective, hedging relationship, effectiveness assessment) should be prepared at inception.

---

## F. Structured AI Prompt

### Appendix: AI Prompt for FX Hedge Spreadsheet Reconstruction

---

```
# GOAL

Build a complete, production-ready Excel workbook modeling four FX hedging strategies 
for a EUR-denominated receivable. The workbook must include named ranges, color-coded 
sections, formula-driven outputs, a sensitivity table, and verification checks. Use 
the exact variable names and values specified below. Do not infer or substitute values.

---

# INPUT VARIABLES

All scenario data is explicitly defined. Use these values in named cells with the 
exact range names listed.

Named Range     | Value          | Description
----------------|----------------|----------------------------------------------
USD_TARGET      | 4,500,000      | USD-equivalent receivable target (given input)
S0_in           | 1.1544         | EUR/USD spot rate at inception (April 2, 2026)
F0_in           | 1.0875         | 1-year EUR/USD forward rate (OTC, course scenario)
R_USD           | 0.03625        | USD 1-year interest rate (Federal Reserve, April 2026)
R_FC            | 0.02000        | EUR 1-year interest rate (ECB, February 2026)
T_DAYS          | 365            | Days to settlement
K_PUT           | 1.1544         | EUR put option strike price (set ATM = S0_in)
K_CALL          | 1.1544         | EUR call option strike price (reference only)
PREM_PUT        | 0.015          | Put option premium per EUR (USD per EUR)
PREM_CALL       | 0.018          | Call option premium per EUR (reference only)

Derived assumption (not a direct input — formula-driven):
FC_AMT          = USD_TARGET / S0_in  =>  3,898,128.90 EUR
F0_CIP          = S0_in * (1 + R_USD) / (1 + R_FC)  =>  ~1.1728

---

# COLOR CODING CONVENTION

Apply background fill colors to ALL cells in each section:
- YELLOW  (#FFFF00)  = Inputs (cells containing named range values above)
- BLUE    (#BDD7EE)  = Assumptions (FC_AMT, F0_CIP — formula-derived from inputs)
- GREEN   (#C6EFCE)  = Formulas / calculation steps (all intermediate and output formulas)
- GRAY    (#D9D9D9)  = Summary outputs / KPIs (final locked-in results, summary table)

Label the color convention in a legend row at the top of the sheet.

---

# SPREADSHEET STRUCTURE

## Sheet 1: Hedge Model

### SECTION 1 — INPUTS
- Create a labeled table with columns: [Variable Name] | [Value] | [Source / Notes]
- Apply named ranges to all input cells using Excel Name Manager
- Yellow fill for all input value cells
- Blue fill for FC_AMT and F0_CIP (derived assumptions)
- Include a verification cell: FC_AMT * S0_in — should equal USD_TARGET ($4,500,000)

### SECTION 2 — FORWARD HEDGE
Formula steps:
  [a] USD_FORWARD = FC_AMT * F0_in
Label result: "FORWARD HEDGE RESULT — LOCKED IN, no exposure to S_T"
Note: This value is fixed regardless of the spot rate at maturity.

### SECTION 3 — MONEY MARKET HEDGE (3-step)
Formula steps:
  [a] EUR_PV    = FC_AMT / (1 + R_FC)          — borrow PV of EUR receivable
  [b] USD_SPOT  = EUR_PV * S0_in               — convert at spot
  [c] USD_MM    = USD_SPOT * (1 + R_USD)        — invest at USD rate for 1 year
Label result: "MONEY MARKET HEDGE RESULT — LOCKED IN"
Add parity check row: USD_MM - USD_FORWARD
Add explanatory note: "Difference reflects CIP deviation — F0_in = 1.0875 does not satisfy 
CIP given R_USD and R_FC. CIP-implied forward = F0_CIP ≈ 1.1728. This is a scenario 
inconsistency, not a formula error."

### SECTION 4 — OPTION HEDGES

#### PUT HEDGE
Formula steps:
  [a] TOTAL_PREM_PUT  = FC_AMT * PREM_PUT
  [b] FV_PREM_PUT     = TOTAL_PREM_PUT * (1 + R_USD)
  [c] PUT_FLOOR       = FC_AMT * K_PUT - FV_PREM_PUT
  
Payoff logic (used in sensitivity table):
  If S_T < K_PUT:  Net proceeds = FC_AMT * K_PUT - FV_PREM_PUT   (put exercised)
  If S_T >= K_PUT: Net proceeds = FC_AMT * S_T - FV_PREM_PUT     (put expires)
  Excel: = FC_AMT * MAX(K_PUT, S_T) - FV_PREM_PUT

Label result: "PUT FLOOR — minimum net USD proceeds"

#### CALL HEDGE (Reference Only)
  [a] TOTAL_PREM_CALL = FC_AMT * PREM_CALL
  [b] FV_PREM_CALL    = TOTAL_PREM_CALL * (1 + R_USD)
Add note: "Call hedge applies to EUR payables, not this receivable. Shown for completeness."

### SECTION 5 — SENSITIVITY ANALYSIS

Generate an 11-row table with S_T values from S0_in * 0.95 to S0_in * 1.05 in 1% steps:
  S_T increments: [0.95, 0.96, 0.97, 0.98, 0.99, 1.00, 1.01, 1.02, 1.03, 1.04, 1.05]
  Applied: S_T = S0_in * multiplier

Columns in sensitivity table:
  1. EUR/USD at Maturity (S_T)           — formula: S0_in * step_multiplier
  2. No Hedge (USD Proceeds)             — formula: FC_AMT * S_T
  3. Forward Hedge (USD Proceeds)        — formula: USD_FORWARD (constant)
  4. MM Hedge (USD Proceeds)             — formula: USD_MM (constant)
  5. Put Hedge (USD Proceeds)            — formula: FC_AMT * MAX(K_PUT, S_T) - FV_PREM_PUT
  6. Put vs. No-Hedge Advantage          — formula: Put Hedge - No Hedge

Add a line chart (Insert > Line Chart) plotting columns 2-5 against column 1 (S_T on X-axis).
Chart title: "FX Hedge Strategy Comparison — EUR/USD Sensitivity"

### SECTION 6 — SUMMARY OUTPUT (Gray fill)
Display final KPIs:
  - Forward Hedge — Locked USD Proceeds:    [USD_FORWARD]
  - Money Market Hedge — Locked Proceeds:   [USD_MM]
  - Put Option — Floor Proceeds (net):      [PUT_FLOOR]
  - CIP Parity Gap (MM - Forward):          [USD_MM - USD_FORWARD]
  - Best strategy if EUR depreciates:       "MM Hedge / Forward Lock"
  - Best strategy if EUR appreciates:       "Put Hedge (retains upside)"
  - Hedge Recommendation:                   "EUR Put Option — see Stage 4 memo"

---

# VERIFICATION CHECKS

Include the following verification rows (label with "CHECK" prefix):

CHECK 1 — USD Notional: FC_AMT * S0_in  — should equal USD_TARGET ($4,500,000)
CHECK 2 — CIP Forward: S0_in * (1 + R_USD) / (1 + R_FC) — display F0_CIP, compare to F0_in
CHECK 3 — Parity Gap: USD_MM - USD_FORWARD — document and explain deviation
CHECK 4 — Put Floor: FC_AMT * K_PUT - FV_PREM_PUT — confirm matches PUT_FLOOR cell
CHECK 5 — Breakeven S_T: K_PUT - (FV_PREM_PUT / FC_AMT) — display the exact S_T at which put = no-hedge (~1.1389)
CHECK 6 — Sensitivity Table: Verify S_T at row 6 (multiplier = 1.00) equals S0_in exactly

---

# SHEET 2: Notes & Assumptions

Create a second sheet with:
- Color coding legend (Yellow/Blue/Green/Gray with descriptions)
- Assumption documentation for each judgment call:
    - FC_AMT derivation rationale
    - Interest rate basis (simple annual, not continuous)
    - Option premium FV methodology
    - CIP deviation explanation
    - Bid-ask spread exclusion
- Data source table:
    - Spot rate: Investing.com, April 2, 2026
    - Forward rate: FIN-321 course scenario materials
    - R_USD: Federal Reserve / Trading Economics, April 2026
    - R_FC: ECB, February 2026
    - Option premiums: FIN-321 course scenario materials

---

# FORMATTING REQUIREMENTS

- Font: Arial throughout, 11pt default
- Column A: 35 characters wide (labels)
- Column B: 18 characters wide (values)
- Column C: 50 characters wide (notes/sources)
- Header rows: Bold, dark fill with white text
- Section headers: Bold, 12pt, with a thick top border
- All USD values: $#,##0.00 number format
- All rate values: 0.0000 number format (4 decimal places)
- All percentage values: 0.00% format
- Freeze panes at row 5 (below legend and title rows)

---

# EXPORT

Save as: [LastName]-[FirstName]-stage2-model-rebuilt.xlsx
Ensure all named ranges are registered in Excel Name Manager.
Confirm zero formula errors before delivery.
Run a formula recalculation pass to verify all cells display computed values, not strings.
```

---

## Extra Credit: Areas for Further Study & Improvement

### 1. AI Skills & Automation

The current model is a static snapshot — inputs are fixed, outputs are computed once, and scenarios are manually defined. AI tools such as Claude with web search, or a Python-based automation pipeline, could transform this into a dynamic, on-demand system. Specifically, a Claude Skill or Code Interpreter workflow could pull live EUR/USD spot rates, ECB and Fed policy rates, and ATM option implied volatility from public APIs (e.g., Yahoo Finance, FRED, CME Group) at the start of each session, automatically populate the named input cells, and regenerate the model without user intervention. More ambitiously, a Monte Carlo simulation layer — sampling from a lognormal EUR/USD distribution calibrated to historical volatility — could replace the deterministic ±5% sensitivity table with a full probability distribution of hedge outcomes. This would enable the CFO to see not just "what if EUR moves 5%" but "what is the 5th percentile USD outcome under the put hedge, and how does it compare to the forward?" This type of simulation-driven risk reporting is standard at Tier 1 banks and large corporate treasuries, and is increasingly accessible via AI-assisted coding.

### 2. Multi-File Reasoning and GitHub Version Control

One of the most underappreciated capabilities of modern AI systems is multi-file reasoning — the ability to read a technical specification (Stage 3), a model file (Stage 2), and a prompt document (Stage 4 Section F) simultaneously, identify inconsistencies, and flag divergences before they propagate into errors. In this project, the CIP deviation between F0_in and F0_CIP was caught and documented manually — but an AI system with access to all three files could automatically flag this type of internal inconsistency as a pre-flight check before model delivery. GitHub serves as the backbone of this workflow: committing each stage as a versioned artifact creates an auditable trail showing not just the final output but every intermediate decision, formula revision, and assumption update. In a corporate treasury or audit context, this matters enormously. Under ASC 815 hedge accounting, firms must demonstrate that hedges were designated and documented at inception — a Git commit timestamped to the booking date is a credible, tamper-evident record of that designation. The combination of AI-assisted consistency checking and Git-based version control represents a significant upgrade over the current industry norm of emailed spreadsheet attachments with version numbers in the filename.

### 3. Accounting & Audit Integration

The hedge accounting implications of this project extend well beyond the analytical model. Under ASC 815 (U.S. GAAP) and IFRS 9, a qualifying cash flow hedge of a foreign-currency receivable allows changes in the fair value of the hedging instrument (here, the EUR put) to be recognized in Other Comprehensive Income rather than flowing directly through earnings — deferring volatility until the hedged transaction settles. To qualify, the firm must prepare formal hedge designation documentation at inception: the risk management objective, the hedging relationship, the hedged item (the EUR receivable), the hedging instrument (the ATM put), and the method for assessing effectiveness. This documentation is not optional — without it, mark-to-market changes hit the income statement each quarter, creating the very earnings volatility the hedge was designed to avoid. GitHub's version-controlled commit history is an ideal vehicle for this documentation requirement. A commit timestamped to April 2, 2026 — containing the Stage 1 memo, Stage 2 model, Stage 3 spec, and the executed hedge terms — constitutes a credible, tamper-evident record that the hedge was designated contemporaneously with the hedged exposure. Auditors reviewing hedge accounting effectiveness can trace every assumption, formula, and market data source through the commit log without relying on the analyst's after-the-fact reconstruction. This is a meaningful improvement over the current industry norm of email chains and shared-drive spreadsheets, and it directly connects the Stage 1–4 workflow of this project to real-world accounting and audit practice.

---

*End of Stage 4 Deliverable — Vanessa Huang | FIN-321 | April 28, 2026*
