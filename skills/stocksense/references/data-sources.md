# Where to find each figure

Read this before the first fetch. It saves wasted calls and keeps derived numbers honest.

## Contents
1. Screener.in (primary)
2. Tickertape, Moneycontrol, others
3. Derived metrics — formulas
4. Banks, NBFCs and insurers — what to use instead
5. What to do when a source fails

---

## 1. Screener.in (primary)

**URLs**
- Consolidated: `https://www.screener.in/company/<NSE_SYMBOL>/consolidated/`
- Standalone: `https://www.screener.in/company/<NSE_SYMBOL>/`
- BSE-only companies: use the numeric BSE code in place of the symbol.
- Not sure of the symbol? WebSearch `screener <company name>` and take the screener.in URL from the results.

**What one page gives you** (ask WebFetch for these exact labels):
- **Top ratios:** Market Cap, Current Price, High / Low (52-week), Stock P/E, Book Value, Dividend Yield, ROCE, ROE, Face Value.
- **Quarterly Results** (~12 quarters): Sales, Operating Profit, OPM %, Other Income, Interest, Depreciation, PBT, Net Profit, EPS.
- **Profit & Loss** (annual, ~10+ years and TTM): same lines plus Dividend Payout %. Underneath it, ready-made tables: **Compounded Sales Growth**, **Compounded Profit Growth** (10/5/3 yrs, TTM), **Stock Price CAGR**, **Return on Equity** (10/5/3 yrs, last year).
- **Balance Sheet:** Equity Capital, Reserves, Borrowings, Other Liabilities, Fixed Assets, CWIP, Investments, Other Assets.
- **Cash Flows:** Cash from Operating / Investing / Financing Activity, Net Cash Flow.
- **Ratios:** Debtor Days, Inventory Days, Days Payable, Cash Conversion Cycle, Working Capital Days, ROCE %.
- **Shareholding Pattern** (quarterly): Promoters, FIIs, DIIs, Government, Public, No. of Shareholders.
- **Documents:** links to annual reports and concall transcripts / notes — use for earnings-call commentary and management guidance.

**Caveats**
- The peer-comparison table and the median-P/E chart load by script and often don't come through WebFetch. For peers, take the peer list from Tickertape / Moneycontrol, or fetch each peer's Screener page. For the stock's own 5-year average P/E, try Tickertape; if nowhere, flag it.
- Screener's auto "Pros / Cons" lines are machine-generated — use them as leads to check, not as findings.
- CMP is as of the fetch (exchange data may be delayed); say "CMP as fetched".

## 2. Tickertape, Moneycontrol, others

- **Tickertape** — find via WebSearch `tickertape <company>`. Best place for **sector P/E, sector P/B and sector dividend yield** shown beside the stock's own; also peers and some ownership trends. Pages are script-heavy, so WebFetch may return only part — ask for specific labels.
- **Moneycontrol** — ratios pages (current ratio, interest coverage, EV/EBITDA), shareholding including **promoter pledge**, peers, news.
- **Trendlyne** — useful cross-check for promoter pledge % and FII/DII trends.
- **NSE / BSE** — authoritative for shareholding and corporate announcements, but usually block automated fetches. Try once; don't retry.
- **Company sources** — annual report, investor presentation, earnings-call transcript: guidance vs delivery, segment data, capex plans, and lender metrics (section 4).
- **Insider and promoter trades** — SAST and insider-trading (PIT) disclosures: Trendlyne and Moneycontrol summarise them; the original filings sit in the company's exchange announcements. Note who traded, buy or sell, how much, and any stated reason.
- **Bulk and block deals** — Moneycontrol and Trendlyne deal pages (the NSE/BSE originals often block fetches).
- **News and macro** — Moneycontrol, Economic Times, Business Standard, Mint for company and sector news; RBI (policy rate, credit data), MOSPI (CPI, GDP) and PIB (government announcements) for macro figures. See `research-desks.md`.

Cross-check CMP, P/E, ROE, D/E and promoter holding across two sources where possible. If two sources disagree by more than a little, show both and say why they might differ (consolidated vs standalone, TTM vs last fiscal year, fetch timing).

## 3. Derived metrics — formulas

Computing from fetched components is fine; label the result "(computed from Screener data)". Never plug in a component you didn't find.

| Metric | Formula / Screener mapping |
| --- | --- |
| CAGR | (end ÷ start)^(1 ÷ years) − 1 — or read Screener's Compounded Growth tables directly |
| EBITDA margin | Screener **OPM %** (operating profit before other income, depreciation, interest, tax) |
| Net profit margin | Net Profit ÷ Sales |
| EPS YoY | Quarter EPS vs the same quarter a year earlier |
| Debt-to-equity | Borrowings ÷ (Equity Capital + Reserves) |
| Interest coverage | (Operating Profit + Other Income − Depreciation) ÷ Interest |
| Free cash flow | Cash from Operating Activity − capex. Capex appears as "Fixed assets purchased" in the detailed cash-flow view or in the annual report. Don't substitute total investing cash flow — it includes investments and other items. If capex can't be isolated, flag FCF and show operating cash flow alone, labelled as such. |
| EV / EBITDA | (Market Cap + Borrowings − Cash & equivalents) ÷ Operating Profit. Prefer a quoted figure from Tickertape/Moneycontrol; compute only if you have cash & equivalents. |
| Payout ratio | Screener **Dividend Payout %**, or DPS ÷ EPS |
| ROE / ROCE 3-yr & 5-yr average | Average of the yearly values in Screener's ROE table and Ratios → ROCE % |

## 4. Banks, NBFCs and insurers — what to use instead

For lenders, borrowed money is the raw material, so D/E, EBITDA, EV/EBITDA, current ratio and FCF mislead. Say you've switched metrics, then use:

| Area | Use | Rough read |
| --- | --- | --- |
| Valuation | **P/B** (or P/ABV) first, P/E second | vs sector & own history, as usual |
| Profitability | **ROA**, ROE, **NIM** | ROA > 1% good · 0.5–1% average · < 0.5% weak |
| Asset quality | **GNPA %, NNPA %**, provision coverage (PCR), credit cost | lower and falling is better; rising NPAs = watch |
| Funding (banks) | **CASA ratio**, deposit growth | higher CASA = cheaper funding |
| Capital | **Capital adequacy (CRAR)** for banks/NBFCs; **solvency ratio** for insurers | compare with the current RBI / IRDAI minimum and say how much headroom there is |
| Growth | loan book / AUM growth, NII growth, PAT growth | same growth words as other companies |
| Insurers | VNB margin & persistency (life); combined ratio (general) | |

Sources: the bank's quarterly investor presentation and results press release, Moneycontrol and Tickertape ratio pages. Screener shows the P&L in lender format (Revenue, Interest, Financing Profit, Financing Margin %) but not NPAs or CASA.

In the Deep Dive template, put lender metrics in the same tabs: NPAs, CASA and CRAR go in **Health**; ROA and NIM in **Returns**; P/B leads **Valuation**. Relabel rows; don't leave EBITDA rows showing "not applicable" everywhere.

## 5. When a source fails

- One source blocked → move to the next in priority order; don't retry the same URL.
- A metric missing everywhere → `🚩 Data unavailable — verify at <most likely source>`.
- Live fetch failing across the board → say so at the top: "Live data couldn't be fetched; figures may be outdated — verify before deciding." Set data confidence to Low.
