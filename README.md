# SBA 7(a) Loan Risk Analysis

A community bank wants to grow its SBA small-business lending by 40% and needs to know where the risk is before it does. I used public SBA data on about 300,000 loans to figure out which loans default, how much they cost the bank, and where it makes sense to grow.

The bank (Blue Ridge Community Bank) is a made-up client for this case study. The loan data is real.

Tableau dashboard: [link]

## Data
- SBA 7(a) FOIA loan data from data.sba.gov, loans approved FY2015–2019 (status as of 2026)
- 301,889 loans after filtering and removing duplicates; 224,444 have a final outcome (paid off or charged off)
- Default rate = charged off / (paid in full + charged off). I also calculated how much the bank actually loses after the SBA guarantee, since that ended up mattering more than the default rate itself.

The raw file is too big for GitHub, so download it from the SBA site if you want to rerun the notebook.

## What I found
- Overall, about 9 in 100 finished loans defaulted (8.7%).
- $150K–$350K loans were the riskiest (11.1%). Loans over $1M were the safest (4.0%).
- The real line was 5 years in business (6.7% default), not just "startup."
- Express loans defaulted less than PLP loans (8.1% vs 9.2%), but cost the bank about 3.4x more per dollar lent, because the SBA only guarantees half of an Express loan. The problem is small Express loans, not big ones.
- PLP loans of exactly $150,000 defaulted at 27.9%, much higher than loans just above or below that amount.
- VA/DC/MD defaulted at 10.7% vs 8.7% nationally. Most of that came from out-of-state lenders: local lenders' loans defaulted at 3.8% vs 11.7%.
- Pennsylvania and Ohio looked like the safest nearby states to expand into.
- Bad loans usually got written off around 4.5 years in, and lost about 81% of the loan.

## Recommendations
1. Use a risk tier table (High / Medium / Low) in approval guidelines
2. Keep Express, but add tighter checks or pricing for loans under $150K
3. Double-check loans sized exactly at program limits
4. Grow in the home market first, then look at Pennsylvania
5. Watch loans most closely in years 2–7

## Files
- `SBA_Loan_Analysis_final.ipynb`: cleaning and analysis in Python
- `SBA_Risk_Dashboard_final.twbx`: 6-tab Tableau dashboard
- `SBA_Credit_Committee_Deck.pptx`: 12-slide deck for the credit committee

## How I built it
I led the project and used a set of AI agents (Claude) to speed things up. I came up with the questions and how to break them down, decided what to analyze and what mattered, and reviewed everything. The agents helped draft code, charts, the dashboard and the deck, and did an independent check of all the numbers before I finalized anything.

## Limitations
- About 14% of loans are still active and SBA hides their outcome, so the results rank risk rather than predict it
- No credit scores or financials in the public data
- Losses don't include money recovered later
- I didn't fully test whether requiring collateral lowers defaults, only that it lowers losses

## Tools
Python (pandas, SciPy, matplotlib), Jupyter, Tableau Public, PowerPoint, Claude
