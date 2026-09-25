# Blended Mortgage Calculator

Branded for OurHappyValleyHome.com, with the Equal Housing Opportunity logo in the footer (embedded in the page).

Single-file calculator (`index.html`, no build step) for purchases where the buyer assumes the seller's first mortgage and covers the equity gap with cash plus a second lien. It compares the blended structure against a new first mortgage at the market rate.

## Inputs

| Group | Fields |
|---|---|
| Listing | Purchase price, buyer cash toward equity |
| Assumable first lien | Loan type (FHA / VA / USDA / Conventional), rate, unpaid balance, **time left (years + months)**, listed P&I (optional cross-check), annual MIP/MI, assumption transaction fee (default $2,300: $200 upfront + $2,100 due at the servicer's Clear to Close), VA funding fee % (VA only) |
| Second lien | Rate, term, interest-only period, closing costs |
| Carrying costs | Annual taxes, annual insurance, monthly HOA |
| Comparison loan | Market rate, term, PMI %, closing costs |

## Outputs

- Blended rate (balance-weighted), cash-flow rate (yield across both liens' full schedules), and payment-equivalent single-loan rate
- Capital stack: first lien / second lien / cash, with % of price, rate and term left
- First-month PITI, side by side with a new loan
- Lifetime savings: debt-free date, total P&I, interest, mortgage insurance and fees to payoff, since the assumed loan usually has fewer than 30 years left
- Holding-period cost: interest, mortgage insurance, fees, principal paid, ending balance
- Cash to close, with the assumption transaction fee split into upfront and Clear to Close amounts
- Warnings: listed P&I that doesn't match balance/rate/term, CLTV above 90%, mismatched lien payoff dates, cash exceeding the gap

## Prefill from a link

Query parameters fill the form, so a listing page or CRM can link straight into a scenario:

```
index.html?price=425000&balance=268000&rate=3.25&years=26&months=6&pi=1258&type=FHA&feeUpfront=200&feeCtc=2100&down=40000&rate2=8.5&term2=25&market=6.5&taxes=6200&ins=1500&hoa=0
```

## Modeling assumptions

- The remaining term drives first-lien amortization. Listed P&I is used only as a cross-check.
- MIP/MI on the assumed loan is charged monthly on the current balance for the whole period.
- PMI on the comparison loan drops when the scheduled balance reaches 78% of the purchase price.
- Prepaids, escrow reserves, lender credits, seller concessions, title and transfer taxes are excluded.
- Lifetime figures assume every scheduled payment is made to payoff, with no prepayment or refinance.
- Buyer cash above the equity gap is not applied to the assumed balance.

The default figures are examples, not data from any listing.
