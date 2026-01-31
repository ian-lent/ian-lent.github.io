# Earnings Surprises and Share Price Reactions  
### A Pilot Event Study Using Refinitiv IBES Data (Walmart)

## Overview
This project analyzes how quarterly earnings surprises relate to short-term share price reactions, with a focus on whether earnings **misses** tend to create asymmetric downside reactions and potential entry opportunities. The initial analysis is structured as a pilot case study using Walmart (WMT), leveraging Refinitiv IBES historical earnings surprise data.

The broader motivation is to understand whether valuation and growth expectations (to be incorporated in later iterations) amplify or dampen market reactions to earnings outcomes, and whether post-earnings dislocations systematically revert over time.

## Research Questions
- How closely are EPS surprises correlated with short-term share price reactions?
- Are earnings misses punished more aggressively than beats are rewarded?
- Does the magnitude of a surprise matter more than its sign?
- Do large misses historically present attractive entry points, on average?

This notebook focuses on **descriptive and exploratory analysis** as a foundation for a larger multi-company study.

## Data Sources
### Earnings Data
- **Source:** Refinitiv IBES  
- **Content:**  
  - Quarterly EPS actuals  
  - Consensus mean estimates  
  - EPS surprise (%)  
  - Refinitiv-calculated 7-day price reaction  
- **Coverage:** Approximately 5 years of quarterly data for Walmart (WMT)

### Price Data
- For this pilot, the analysis relies on Refinitiv’s **7-day price reaction** metric.
- Daily price-level event studies (e.g., EMAs, forward returns) are planned for future versions once a stable daily price source is integrated.

## Methodology
1. Clean and structure quarterly earnings surprise data.
2. Exclude fiscal-year aggregates to focus on discrete quarterly events.
3. Visualize:
   - EPS surprises over time
   - Short-term price reactions over time
   - Surprise magnitude vs. price reaction
4. Test asymmetry between earnings beats and misses.
5. Run simple regressions to quantify the relationship between surprise size and price response.

## Key Outputs
- Time-series bar charts of EPS surprises (beat vs. miss clearly visualized)
- Time-series plots of post-earnings price reactions
- Scatter plots linking surprise magnitude to market response
- Summary statistics comparing reactions to beats vs. misses
- Regression results estimating sensitivity of price reactions to earnings surprises

## Current Limitations
- Single-company focus (WMT) for pilot analysis
- Short-horizon price reaction only (7-day window)
- No explicit valuation or growth multiple controls yet
- Event dates approximated at the monthly level (to be refined)

## Planned Extensions
- Expand to a cross-section of S&P 500 companies
- Incorporate valuation metrics (EV/EBITDA, P/E, growth expectations)
- Perform longer-horizon post-earnings return analysis
- Test whether high-multiple stocks exhibit more asymmetric downside
- Segment results by sector and market regime

## Disclaimer
This project is for educational and analytical purposes only. All analysis reflects personal opinion and does not constitute investment advice.
