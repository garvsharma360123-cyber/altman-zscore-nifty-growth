# Altman Z″-Score Analysis — Nifty Growth Sector

A Power BI dashboard applying the Altman Z″-Score (bankruptcy/distress risk
model) to 20 Indian listed companies — 15 Nifty large-caps across IT, FMCG,
auto, pharma, and healthcare, plus 5 companies with real financial stress
added for contrast (including one currently in insolvency proceedings).

**File:** `Report.pbix` — open in Power BI Desktop to explore interactively.

---

## Dashboard Pages

### Page 1 — Z″-Score & EBIT Margin Quadrant
![Z Score and EBIT Margin quadrant](page1-zscore-ebit-quadrant.png)

Scatter plot: every company's EBIT Margin vs. Z″-Score.

- **Vertical line (Z″ = 2.6):** the Safe-zone threshold
- **Horizontal line (0.18):** median EBIT margin across all 20 companies

**Top-right** = strong margins + safe balance sheet (Divi's, TCS).
**Top-left** = profitable but more leveraged (Vedanta).
**Bottom-left** = weak on both (Jaiprakash Associates).

**Outlier:** Vodafone Idea shows an EBIT margin over 100% — not a real
operating result. It's a one-time ~₹57,595 Cr AGR-related gain in Q4 FY26.
Its actual day-to-day operations are still loss-making.

### Page 2 — Sector Comparison
![Average Z Score by sector](page2-sector-wise-zscore.png)

Average Z″-Score by sector, colored by Safe/Grey/Distress mix. **Filtered to
only IT Services, Automobiles, FMCG, and Pharmaceuticals** — the four
sectors with more than one company. The other 7 sectors have exactly one
company each, so their "average" would just be that single company's score,
not a real comparison.

**Takeaway:** IT Services and Pharma score consistently high (low leverage,
stable earnings). Automobiles has the widest spread.

### Page 3 — Distress & Grey Zone Drill-Down
![Distressed and Grey zone companies](page3-distressed-grey-zone.png)

Two side-by-side charts, showing only the 4 flagged companies (Jaiprakash
Associates, Vodafone Idea, TVS Motor, Vedanta) — Z″-Score on the left, EBIT
Margin on the right — so it's easy to see *why* each one was flagged without
hunting through the full 20-company chart.

**Validation:** Jaiprakash Associates (currently under NCLT insolvency
proceedings, being delisted June 2026) and Vodafone Idea (negative net worth
for years) are the two companies the model flags hardest. Both are real,
independently known distress cases — the model catching them using only
public balance sheet ratios is the strongest proof point in this project.

---

## Why Z″-Score, and Why Book Value for X4

Used the **Z″-Score** (not the original 5-variable Z-Score) since it drops
the Sales/Total Assets term — a term that would unfairly reward asset-light
IT companies just for their business model rather than lower actual risk,
given this dataset mixes IT services with capital-heavy manufacturing.

X4 (leverage ratio) uses **Book Value of Equity**, not Market Cap. The
market-cap version produced scores like 110 for Divi's Labs — technically
correct math, but meaningless as a distress signal, since it mostly reflects
how expensive the stock is, not how much debt cushion the company has.

```
Z″ = 6.56·(WC/TA) + 3.26·(RE/TA) + 6.72·(EBIT/TA) + 1.05·((TA−TL)/TL)
```
Zones: **Safe** > 2.6 · **Grey** 1.1–2.6 · **Distress** < 1.1

---

## Key Limitations

- Single-year snapshot (FY Mar-2026) — no trend over time
- Working Capital figures are approximations for several companies (from
  balance-sheet-health snapshots, not literal CA−CL from filings)
- 4 companies (Eicher Motors, Sun Pharma, Divi's Labs, Apollo Hospitals) rely
  on third-party aggregator data rather than a full primary balance sheet pull
- Not investment advice — this measures distress risk, not overall investment
  quality (growth, valuation, management aren't captured here)

## Data Sources

[Screener.in](https://www.screener.in) (primary) · [Simply Wall St](https://simplywall.st) · [Tipranks](https://www.tipranks.com)

## How to Open

1. Download `Report.pbix`
2. Open in Power BI Desktop
