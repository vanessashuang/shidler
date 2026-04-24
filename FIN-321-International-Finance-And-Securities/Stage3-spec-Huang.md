# FX Hedge Analysis: EUR Receivable – Technical Specification

**Created by:** Vanessa Huang
**Updated by:** Vanessa Huang
**Date Created:** April 24, 2026
**Date Updated:** April 24, 2026
**Version:** 1.0
**LLM Used:** Claude Sonnet 4.6

**Role:** Financial Analyst / Treasury Analyst
**Audience:** CFO or Director of Treasury

**Purpose:** Provide a professional, quantitative specification documenting the analytical structure of the Stage 2 FX hedge model and articulating a refined, improved version suitable for reconstruction by a treasury analyst or AI model-builder.

---

## 1. Problem Statement

A U.S.-based solar equipment importer holds a EUR-denominated receivable equivalent to $4,500,000 USD (at inception spot) due in 12 months. The firm's functional currency is USD, exposing it to potential loss if EUR depreciates against the dollar between the booking date (April 2, 2026) and the settlement date (approximately April 2, 2027).

The EUR notional is back-calculated from the USD target: at a spot rate of $1.1544/EUR, the receivable equals approximately €3,898,129. The primary risk is that EUR/USD falls at maturity, reducing USD receipts below the $4,500,000 target. In the worst case of the modeled range (S_T = S₀ × 0.95 ≈ 1.0967), an unhedged position would yield approximately $4,275,000 — a shortfall of roughly $225,000 relative to the USD target. A secondary objective is to retain upside participation if EUR strengthens.

This specification documents the analytical framework for evaluating four alternatives: no hedge, forward hedge, money market hedge, and EUR put option hedge — with a sensitivity analysis across a ±5% EUR/USD range.

---

## 2. Inputs (Known Variables)

| Named Range   | Description                              | Unit        | Value         | Source                                    |
|---------------|------------------------------------------|-------------|---------------|-------------------------------------------|
| `USD_TARGET`  | USD-equivalent receivable target         | USD         | 4,500,000     | Stage 1 memo                              |
| `FC_AMT`      | EUR notional (back-calculated)           | EUR         | 3,898,128.90  | Derived: `USD_TARGET ÷ S0_in`            |
| `S0_in`       | EUR/USD spot rate at inception           | USD per EUR | 1.1544        | Investing.com, April 2, 2026              |
| `F0_in`       | 1-year EUR/USD forward rate              | USD per EUR | 1.0875        | FIN-321 course scenario materials         |
| `R_USD`       | USD 1-year interest rate                 | Annual %    | 3.625%        | Federal Reserve / Trading Economics       |
| `R_FC`        | EUR 1-year interest rate                 | Annual %    | 2.000%        | ECB policy rate, February 2026            |
| `T_DAYS`      | Days to settlement                       | Days        | 365           | 1-year receivable                         |
| `K_PUT`       | EUR put option strike price              | USD per EUR | 1.1544        | Set at-the-money (= S0_in)                |
| `K_CALL`      | EUR call option strike price             | USD per EUR | 1.1544        | Set at-the-money (= S0_in); reference only|
| `PREM_PUT`    | Put option premium per EUR               | USD per EUR | 0.015         | FIN-321 scenario materials                |
| `PREM_CALL`   | Call option premium per EUR              | USD per EUR | 0.018         | FIN-321 scenario materials; reference only|

**Derived assumption (not a direct input):**
`F0_CIP` (CIP-implied forward) = `S0_in × (1 + R_USD) / (1 + R_FC)` ≈ 1.1728. This diverges from the scenario-provided `F0_in` = 1.0875, producing a ~$332,476 parity gap documented in Section 3 of the model.

---

## 3. Assumptions & Constraints

- **Interest rate basis:** Rates are applied as annual simple interest over 365 days using the factor `(1 + R)`. Continuous compounding and ACT/360 conventions are not used; this aligns with standard FIN-321 textbook treatment.
- **FC_AMT derivation:** The EUR notional is a formula-driven assumption (`USD_TARGET ÷ S0_in`), not a directly stated input. It updates automatically if `S0_in` is revised.
- **Option pricing:** Premiums are scenario-provided flat rates, not Black-Scholes or market-quoted values. They represent a per-unit cost in USD, paid upfront at inception.
- **Option premium future value:** Each premium is compounded forward using simple interest (`Total_Premium × (1 + R_USD)`) to convert the upfront cost into a year-end equivalent, making it directly comparable to proceeds received at maturity.
- **Forward rate:** `F0_in` = 1.0875 does not satisfy covered interest parity (CIP) given the stated `R_USD` and `R_FC`. Both the forward hedge and money market hedge are computed independently and the gap is explicitly flagged — it is a scenario-embedded inconsistency, not a formula error.
- **Bid-ask spreads and transaction costs:** Excluded. All rates are mid-market benchmarks. This understates real execution costs.
- **Call option:** Included for reference only. A EUR call hedges a payable, not a receivable. It is not part of the primary hedge decision but is shown for completeness.
- **Exchange rate convention:** All rates are expressed as USD per EUR throughout.

---

## 4. Calculation Flow

### Step 1 — Forward Hedge

1. Multiply `FC_AMT` by `F0_in` to compute locked-in USD proceeds.
2. This result is fixed regardless of `S_T`; it eliminates all FX exposure.

*Result: `USD_FORWARD = FC_AMT × F0_in = $4,239,215`*

### Step 2 — Money Market Hedge

1. Compute the present value of the EUR receivable by dividing `FC_AMT` by `(1 + R_FC)`. This is the amount to borrow today in EUR.
2. Convert the EUR borrowing to USD at the spot rate `S0_in`.
3. Invest the resulting USD amount at `R_USD` for one year.
4. The ending USD balance is the money market hedge result — a locked-in amount independent of `S_T`.
5. Compare to the forward result. If `F0_in` satisfied CIP, both methods would produce identical proceeds. The observed $332,476 gap reflects the CIP deviation in the scenario inputs and is documented explicitly.

*Result: `USD_MM = [FC_AMT ÷ (1 + R_FC)] × S0_in × (1 + R_USD) = $4,571,691`*

### Step 3 — EUR Put Option Hedge

1. Compute the total put premium paid today: `FC_AMT × PREM_PUT`.
2. Compound to maturity: `Total_Premium × (1 + R_USD)` to get the future value of the cost.
3. Determine net USD proceeds for any given `S_T`:
   - If `S_T < K_PUT`: exercise the put; sell EUR at `K_PUT`. Net proceeds = `FC_AMT × K_PUT − FV(PREM_PUT)`.
   - If `S_T ≥ K_PUT`: let the put expire; sell EUR at market rate `S_T`. Net proceeds = `FC_AMT × S_T − FV(PREM_PUT)`.
4. The floor (minimum net proceeds) applies when the put is exercised.

*Floor result: `USD_PUT_FLOOR = FC_AMT × K_PUT − FV(PREM_PUT) = $4,439,408`*

### Step 4 — No-Hedge Baseline

For each `S_T` in the sensitivity table, compute unhedged proceeds as `FC_AMT × S_T`. This serves as the benchmark against which hedged strategies are compared.

### Step 5 — Sensitivity Analysis

For each of the 11 `S_T` values ranging from `S0_in × 0.95` to `S0_in × 1.05`, compute USD proceeds under all four strategies and record them in a comparison table. Generate a line chart.

---

## 5. Outputs

| Output                       | Description                                              | Format        | Purpose                                         |
|------------------------------|----------------------------------------------------------|---------------|-------------------------------------------------|
| `USD_FORWARD`                | Locked-in USD proceeds under forward hedge               | Numeric scalar| Certainty benchmark; $4,239,215                 |
| `USD_MM`                     | Locked-in USD proceeds under money market hedge          | Numeric scalar| Parity cross-check; $4,571,691                  |
| `USD_PUT_FLOOR`              | Minimum net USD proceeds under put hedge                 | Numeric scalar| Downside floor; $4,439,408                      |
| `F0_CIP`                     | CIP-implied forward rate                                 | Numeric scalar| Parity deviation diagnostic; 1.1728             |
| `Parity_Gap`                 | MM result minus forward result                           | Numeric scalar| Flags scenario inconsistency; $332,476          |
| `Sensitivity Table`          | USD proceeds by strategy across 11 S_T values            | Table (11 rows × 5 cols) | Scenario comparison and breakeven analysis |
| `Chart_1: Hedge Payoff Chart`| Line chart of USD proceeds vs. S_T for all strategies   | Line chart    | Visual strategy comparison for executive review |
| `Summary KPIs`               | Final locked proceeds, floor, parity gap, best strategies| Summary block | Decision-ready output; feeds Stage 4            |

---

## 6. Model Review — What Worked & What to Improve

### What Worked Correctly

- All four hedge strategies (no hedge, forward, money market, put) compute independently and produce internally consistent results.
- The put payoff logic correctly applies a `MAX(K_PUT, S_T)` condition row-by-row, producing the floor below K_PUT and upside participation above it.
- The premium future value adjustment correctly converts the upfront option cost to a maturity-equivalent, enabling apples-to-apples comparison with other strategies.
- The CIP deviation is explicitly identified, quantified, and explained rather than silently ignored — this is analytically sound and audit-ready.
- Color coding (yellow = inputs, blue = assumptions, green = formulas, gray = outputs) provides clear navigational structure.

### What Should Be Improved

| Issue | Current State | Improved Approach |
|-------|--------------|-------------------|
| **FC_AMT is a derived assumption, not an input** | Back-calculated from USD target ÷ S₀; changes if S₀ changes | In a more rigorous model, FC_AMT should be a primary input (stated contract amount), with a separate USD_EQUIVALENT cell for reference |
| **F0_in violates CIP** | Used as-is with a note | Improved version should include a toggle: use scenario-provided F0_in or CIP-implied F0_CIP, with a clear flag when they diverge |
| **Call option not integrated into sensitivity table** | Shown as reference-only; excluded from chart | A rebuilt model should include a EUR call payoff row in the sensitivity table for completeness, even if it applies to the payable case |
| **No breakeven S_T identified** | Put vs. no-hedge advantage column shows sign change but breakeven is not solved explicitly | Compute and display the exact S_T at which put hedge equals no-hedge: `K_PUT − FV(PREM_PUT)/FC_AMT` |
| **Sensitivity range is fixed at ±5%** | Hard-coded step increments | Improved model should allow user-adjustable range and step size, driven by named input cells |
| **No named ranges in Excel** | Cell references used throughout | Implement Excel named ranges matching the variable names in this spec (e.g., `FC_AMT`, `S0_in`, `F0_in`) to improve auditability and AI-readability |

---

## 7. Sensitivity Plan

The sensitivity analysis varies `S_T` from `S0_in × 0.95` to `S0_in × 1.05` in 11 equal steps of 1.0%, producing `S_T` values from approximately 1.0967 to 1.2121. This range reflects a realistic annual EUR/USD movement; the EUR has historically moved ±5–10% in non-crisis years.

For each `S_T` value, the model computes:
- **No hedge:** `FC_AMT × S_T`
- **Forward hedge:** constant at `USD_FORWARD` (flat line)
- **Money market hedge:** constant at `USD_MM` (flat line)
- **Put hedge:** `MAX(K_PUT, S_T) × FC_AMT − FV(PREM_PUT)`

The resulting line chart displays all four strategies on a single axis. Key visual insights:
- The forward and MM hedge appear as horizontal lines — they lock in proceeds regardless of `S_T`.
- The put hedge mirrors the no-hedge line above `K_PUT` (minus premium cost) and becomes flat below `K_PUT` (the floor).
- The crossover between the put and no-hedge lines identifies the breakeven spot rate.
- The chart communicates to the CFO when the option's insurance value exceeds its cost.

The most decision-relevant comparison is **forward vs. put hedge**: the forward guarantees $4,239,215 with no upside; the put guarantees a floor of $4,439,408 but costs the premium in upside scenarios. This trade-off is the core analytical output.

---

## 8. Limitations & Next Steps

**Analytical limitations of the current model:**
- Implied volatility is excluded; option premiums are scenario-provided flat rates, not market-derived. A Black-Scholes or market-quoted premium could differ materially.
- Dynamic or rolling hedges are not modeled. The analysis assumes a single static hedge held to maturity.
- Credit and counterparty risk on the forward contract is not quantified.
- Accounting treatment (hedge accounting under ASC 815 / IFRS 9) and tax effects are outside scope.
- The CIP violation in the scenario inputs means the forward and money market hedge results are not directly comparable without acknowledging the inconsistency; this is documented but not resolved.
- Bid-ask spreads on spot, forward, and option markets are excluded, understating real execution costs by an estimated 5–15 basis points per leg.

**Next steps — Stage 4:**
This specification serves as the primary input to the Stage 4 AI prompt. A well-structured prompt will reference the named ranges in Section 2, the calculation logic in Section 4, and the improvement list in Section 6 to instruct the AI to build a corrected, production-ready version of this model. The key improvement targets — named ranges, a CIP-toggle input, an explicit breakeven calculation, and a fully integrated call option row — should be specified as explicit output requirements in the Stage 4 prompt.

---
