# Portfolio Performance & Trade Execution

Two analyses of the same personal equity account, from Fidelity exports.

**[Trade Execution Analysis](Trade%20Execution%20Analysis.ipynb)** — every
completed round-trip, Sep 2024 to Aug 2026. Hit rate, payoff ratio, expectancy,
holding-period behaviour and profit concentration.

**[Portfolio Performance](Portfolio%20Performance.ipynb)** — time-weighted
monthly returns and risk metrics, Jul 2024 to Jan 2026. Bounded by the balance
export, which covers that window only.

## Returns and ratios, not balances

Every figure in both notebooks is a percentage, a ratio or a count. Account
balances are read to compute return series and are never displayed, and no
instrument is named. The size of the account and the identity of the positions
are not part of either question.

## Method

**Returns.** Monthly return divides period P&L by the capital actually at risk:

```
r = (market change + dividends + interest − fees) / (beginning balance + deposits)
```

Dividing by the capital base rather than the beginning balance stops a month
containing a deposit from reporting an inflated return, so the series measures
the portfolio rather than the funding schedule.

**Round-trips.** Fidelity exports no lot assignment, so buys are matched to
sells first-in-first-out. Totals are right; the split across individual
round-trips may differ from the broker's where specific lots were sold.

## Two parsing problems worth naming

Both exports are reports rendered as CSV, not data files, and both punish a
naive `read_csv`.

**The balance export** ends in a `Total` row and a multi-line legal disclaimer,
all of which parse as data — 18 of 37 rows were not months. An earlier version
of this analysis divided its hit rate by every row rather than by the months and
published roughly half the true figure. The `Total` line can also parse as an
extra month carrying a fabricated return. Rows now survive only if the first
column parses as `%b %Y`, checked before any metric is computed and asserted
after.

**The transaction history** is capped by date range, so it arrives as several
overlapping files. Concatenating and dropping duplicate rows looks obvious and
is wrong: two genuine fills of the same size at the same price on the same day
are indistinguishable from one row appearing twice, so deduplication deletes
real trades — three of them here. Overlaps are resolved a day at a time
instead, taking whichever file has more rows for that date and ignoring the
other.

## Limits

- Short samples. Ratios over this many observations are estimates with wide
  error bars, not settled properties.
- Risk-free rate is zero, which flatters Sharpe and Sortino.
- Drawdown is measured month-end to month-end, so intra-month troughs are
  invisible and the true figure is deeper than reported.
- Per-trade returns are unweighted by size or duration: they describe decision
  quality, not capital growth.
- One account, one investor, one market regime. Nothing here generalises.

## Data

Both notebooks read the newest matching export from `~/Downloads` and need no
code change to refresh:

- `Investment_income_balance_detail*.csv` — Accounts → Performance & Analysis →
  Investment income & balance detail, monthly frequency
- `History_for_Account_*.csv` — Accounts → Activity → download, one file per
  date range
