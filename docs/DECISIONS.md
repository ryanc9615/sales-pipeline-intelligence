# Sales Pipeline Intelligence Tool — Decisions and Parked Ideas

**Baseline date:** 31 October 2026. These are planning choices made to turn the brief into a small, teachable project. No implementation is implied.

| ID | Choice | Reason / trade-off |
|---|---|---|
| D001 | Python + pandas + Streamlit | Teaches core data flow and gives a deployable UI without a separate frontend/backend |
| D002 | One canonical CSV schema | Focuses learning on validation and analytics; arbitrary CRM export mapping deferred |
| D003 | One current-state snapshot | Keeps ingestion beginner-sized; stage history and past-state reconstruction cannot be inferred |
| D004 | GBP; total deal contract value | Removes FX/contract-recognition complexity; forecast is bookings, not accounting revenue |
| D005 | Integer pence + Decimal probabilities; round each weighted deal half up | Exact money and independently auditable forecast sums |
| D006 | Explicit snapshot date and current reporting period | Avoids invisible “today” behaviour and misleading historical simulation |
| D007 | Current pipeline separate from period-eligible pipeline | Overdue and out-of-period deals should not quietly inflate forward forecast / coverage |
| D008 | Closed win rate plus observed creation-cohort conversion | Both are supported by snapshot fields; neither is historical stage-to-stage conversion |
| D009 | Fixed 14-day inactivity and 30-day stage thresholds | Teachable review heuristics; not a learned probability of loss |
| D010 | Small localhost HTTP/JSON exercise | Covers API fundamentals without introducing a CRM integration or another web framework |
| D011 | Documentation-only starter; no prebuilt application | Preserves the learner's opportunity to implement, inspect and debug the whole workflow |
| D012 | Aim at 40 hours in three weeks | A manageable planning baseline; acceptance evidence governs completion |

## PARK FOR LATER

Live CRM adapters / OAuth / pagination; stage histories and true funnel conversion; historical slippage; multiple currencies; recurring-revenue recognition; machine learning and calibrated forecasts; AI summaries; databases; user accounts; React; automated browser testing; elaborate CI/CD; paid hosting; configurable risk thresholds if they delay core delivery.

## Change log template

- **ID / date / phase:**
- **Problem or evidence:**
- **Options and trade-off:**
- **Decision and why:**
- **Effect on scope / hours / calculation semantics:**
- **Files / acceptance criteria to reconcile:**
- **Verification needed / observed:**

Routine reversible choices within this baseline do not need a permission ceremony. Record changes that affect the contract, budget or meaningful design trade-offs.
