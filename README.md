# Camden Council Expenditure Audit

**Problem:** Where does Camden Council's money go, and how much of it is hidden behind redacted beneficiary names?

## Why this matters

Councils publish every payment over £500 so the public can scrutinise how money is spent. But roughly one in six payments has the recipient's name hidden, so nobody outside the council can see who was paid. This analysis measures that gap, which is useful to residents, journalists, councillors and auditors who want to know how much public spending can actually be traced.

## Data

408,317 payments over £500 from the London Borough of Camden, published as open data ([Spend over £500 on data.gov.uk](https://www.data.gov.uk/dataset/camden-council-spend-over-500-gbp)). Payment dates run from **February 2019 to January 2026** *[confirm end date in the notebook]*. The CSV is not stored in this repo, so download it from the link.

## What I did, and what each choice changed

| Decision | Why | Effect |
|---|---|---|
| Replaced 7,111 blank VAT values with 0 | Every other value in that column was 0 | 1.7% of rows filled; no effect on spend totals |
| Dropped 1 row with a blank beneficiary name | One row out of 408,317 could not be grouped by recipient | 408,316 rows analysed |
| Merged every spelling of "redacted" into one group (`REDACTED`, `xxxxREDACTEDxxxx` and others) | Otherwise the hidden spend is split across several rows and looks smaller | 65,000+ payments grouped under one label, now visible as a single £316m total |
| Kept the £31.55m payment to the Greater London Authority (GLA) in the data, but left it out of the supplier chart | It is a statutory levy, not a supplier, and it makes the chart unreadable | About 0.6% of total spend |

**Alternative considered:** dropping the GLA payment entirely. I kept it so the totals still add up to the published data.

## Findings

- **About 16% of payments (roughly one in six) have a redacted beneficiary.** *[confirm exact count in notebook]*
- **Those payments total £316m, about 6% of the £5.6bn spent.** *[confirm total in notebook]*
- Redacted spend is the **third-largest "beneficiary" overall**, after the GLA (£674m) and HMRC payroll (£547m). It is the largest once those two are set aside.
- The largest share of redacted spend (£137m) sits in the "Camden Council" organisational unit. I don't know why; it may be internal transfers or sensitive payments, but the data doesn't say.
- The largest single payment was £31.55m to the GLA (a levy, September 2020).

## Recommendations

1. Councils could publish a **reason code** for each redaction (for example "social care, data protection"), so the public can tell legitimate privacy from avoidable secrecy.
2. Reviewers should look first at the £137m of redacted spend in the "Camden Council" unit.
3. Flag very large one-off payments in the open data so they don't distort totals.

## Limitations

- Only payments over £500 are published.
- The analysis shows *that* names are hidden, not who was paid or why.
- Redaction is often legitimate (for example, protecting individuals receiving care), so a high figure is not evidence of wrongdoing.
- I have not checked whether the same payment appears more than once.

## What worked, what I would change, what I learned

*[Tom: draft in your own words. Suggestions.]*

- **Worked:** writing down each cleaning decision and its effect made the results easy to defend.
- **Would change:** calculate the percentages in the notebook itself, rather than only the totals, and check for duplicate payments.
- **Learned:** a few messy name variants can hide the single biggest item in a dataset.

## How to run

```bash
pip install -r requirements.txt
```
Download the CSV from the link above, save it as `Camden_Council_Spend_Over_500_GBP.csv` next to the notebook, then open the notebook in Jupyter.

**Tools:** Python, pandas, matplotlib, Jupyter.

## Contact

[LinkedIn](https://www.linkedin.com/in/YOUR-HANDLE) | [email]
