# FX Exposure & Hedging Memo: Scenario 1 – U.S. Solar Equipment Importer

**Created by:** Vanessa H. with assistance from Claude AI

**Date Created:** April 2, 2026


**LLM Used:** Claude Sonnet 4.6

---

## Executive Summary

Our firm expects to receive a EUR-denominated payment equivalent to $4,500,000 in one year. With the EUR/USD spot rate at 1.1544 (April 2, 2026), a strengthening U.S. dollar over the next 12 months could materially reduce our USD proceeds. This memo outlines our FX exposure, the associated risks, and three hedging strategies to consider.

---

## Background & Objectives

Our firm faces transactional FX risk on a $4,500,000 EUR receivable due in one year. EUR/USD has been volatile in 2026, ranging from 1.1453 to 1.2019, driven by Middle East geopolitical tensions and diverging central bank policy. The Fed holds rates at 3.625% while the ECB sits at 2.00%, creating a rate differential that pressures the euro.

**Key market inputs (April 2, 2026):**
- EUR/USD Spot: 1.1544
- 1-Year Forward Rate: 1.0875
- USD Interest Rate: 3.625%
- EUR Interest Rate: 2.00%
- Put on EUR (K = 1.1544): $0.015/unit premium
- Call on EUR (K = 1.1544): $0.018/unit premium

---

## Methods

We will evaluate three hedging families:

- **Forward Contract:** Lock in 1.0875 for the full receivable. Eliminates all FX risk but forfeits any upside if the EUR strengthens. Best for firms prioritizing cash flow certainty.
- **Put Option on EUR (K = 1.1544):** Pay $0.015/unit to floor our USD proceeds at the strike. Retains upside if EUR appreciates. Best for firms with moderate risk tolerance.
- **Unhedged:** Accept the spot rate at maturity. Full upside potential, full downside exposure. Only appropriate with high FX risk tolerance and a strong directional view.

---

## Limitations & Next Steps

Rates reflect benchmark policy levels as of April 2, 2026, and may differ from OTC pricing. Option premiums are scenario-provided, not Black-Scholes derived.

- **Stage 2:** Build an Excel model comparing net USD proceeds across a range of EUR/USD outcomes.
- **Stage 3:** Document model architecture for AI-assisted reconstruction.
- **Stage 4:** Select optimal strategy and present final recommendation to the CFO.

---

## References

- Investing.com. (2026, April 2). *EUR/USD Historical Data.*
- Trading Economics. (2026, April 2). *United States Fed Funds Rate.*
- European Central Bank. (2026, February 5). *Monetary Policy Decisions.*
- FIN-321-002 Course Materials – Scenario 1: U.S. Solar Equipment Importer.
