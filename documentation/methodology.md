# UltraTech Cement --- Financial Modelling & DCF Analysis

## Methodology

**Model date:** 11 September 2026\
**Forecast period:** FY27E--FY29E\
**Historical period:** FY24A--FY26A\
**Currency:** ₹ crore unless otherwise stated

------------------------------------------------------------------------

## 1. Objective

This model was built as a practical financial-modelling and valuation
exercise using UltraTech Cement Limited.

The objective is to demonstrate an end-to-end modelling workflow:

1.  Collect and standardise historical financial information from
    company filings.
2.  Translate business operating drivers into forecast assumptions.
3.  Build an integrated income statement, balance sheet and cash flow
    statement.
4.  Build supporting schedules for PP&E/capex, depreciation,
    debt/interest and working capital.
5.  Convert forecast operating performance into free cash flow to the
    firm (FCFF).
6.  Value the business using a discounted cash flow (DCF) framework.
7.  Test valuation sensitivity to WACC and terminal growth.
8.  Apply model QA checks and document assumptions and limitations.

The model is designed as an interview-defensible learning model rather
than a full institutional investment-banking model.

------------------------------------------------------------------------

## 2. Historical financials

FY24A--FY26A historical financial information is sourced primarily from
UltraTech's statutory financial disclosures, annual reports and investor
materials.

A key modelling decision was to use the statutory consolidated **Revenue
from Operations** series consistently rather than mixing statutory
revenue with management's separately presented Net Sales definition.

FY24 comparative figures were also treated carefully because UltraTech's
Kesoram transaction resulted in restatement of financial results from 1
April 2024.

Historical data is entered as source data in `02_Historicals` and then
linked into the forecast statements rather than repeatedly hardcoding
the same values across multiple sheets.

------------------------------------------------------------------------

## 3. Operating-driver approach

The forecast follows the principle:

> **Forecast the business driver where possible, rather than directly
> forecasting the output.**

The main operating drivers are:

-   India grey cement capacity
-   Capacity utilisation
-   Grey cement production
-   Grey cement sales volume
-   Blended realisation per tonne
-   EBITDA per tonne

The operating-driver framework is used to establish a commercially
intuitive forecast path.

### Revenue

Forecast consolidated revenue is anchored to FY26 consolidated revenue
and grown using the model's volume and realisation operating proxies:

**Revenue growth proxy = Volume growth × Realisation growth**

This avoids forcing India grey cement volume multiplied by a per-tonne
realisation to equal consolidated revenue, which would be inappropriate
because the consolidated business includes additional
businesses/geographies and reporting definitions.

### EBITDA

Operating EBITDA is forecast using:

**Operating EBITDA = Sales volume × EBITDA per tonne**

EBITDA per tonne is grown at the assumed annual rate rather than simply
applying a fixed EBITDA margin.

This creates an operating leverage framework that can be stress-tested
through the underlying drivers.

------------------------------------------------------------------------

## 4. Income statement

The forecast income statement is structured as:

**Revenue from Operations**\
→ **Operating EBITDA**\
→ **Other Income**\
→ **EBITDA**\
→ **D&A**\
→ **EBIT**\
→ **Finance Costs**\
→ **PBT**\
→ **Tax**\
→ **PAT**

Historical values are linked from `02_Historicals`.

Forecast revenue and operating EBITDA are linked from `03_Drivers`.

Other income is forecast as a percentage of revenue. Exceptional items
and share of associates/JV are set to zero in the forecast period as
simplifying assumptions.

Tax is modelled as a percentage of PBT.

------------------------------------------------------------------------

## 5. PP&E and depreciation schedule

The PP&E schedule links historical capex and D&A to the balance sheet.

For the forecast period:

**Closing PP&E = Opening PP&E + Capex − D&A**

Forecast capex is held at the model assumption of ₹10,000 crore per
year.

Forecast D&A is approximated as a percentage of opening net PP&E:

**D&A = Opening net PP&E × 6%**

This is deliberately simpler than a full asset-vintage depreciation
schedule. The objective is to maintain integrated three-statement
mechanics without introducing unnecessary model complexity.

------------------------------------------------------------------------

## 6. Working capital schedule

Forecast operating working capital is modelled using revenue/cost-based
ratios:

-   Accounts receivable = % of revenue
-   Inventory = % of operating costs
-   Trade payables = % of operating costs

Net working capital is:

**NWC = AR + Inventory − AP**

The cash flow statement uses:

**Cash flow impact of working capital = − Change in NWC**

Therefore:

-   Increase in NWC → cash outflow
-   Decrease in NWC → cash inflow

The forecast ratios are analyst assumptions and are not intended to
represent management guidance.

------------------------------------------------------------------------

## 7. Debt and interest schedule

The debt schedule begins with FY26 actual consolidated debt.

Forecast debt is increased by the modelled annual debt raise.

Interest expense is calculated using average debt:

**Average Debt = (Opening Debt + Closing Debt) / 2**

**Finance Cost = Average Debt × Assumed Interest Rate**

This approach avoids unnecessary circularity between cash, debt and
interest in the v1 model.

------------------------------------------------------------------------

## 8. Balance sheet

The forecast balance sheet is integrated through:

-   PP&E from the PP&E schedule
-   AR, inventory and AP from the working-capital schedule
-   Cash from the cash flow statement
-   Debt from the debt schedule
-   Other balance-sheet items held constant where a detailed driver was
    not necessary
-   Other equity updated through retained earnings logic

The fundamental accounting identity is:

**Assets = Liabilities + Equity**

A balance-sheet check is included in `10_Checks`.

------------------------------------------------------------------------

## 9. Cash flow statement

The forecast cash flow statement follows:

### Cash flow from operations

**CFO = PAT + D&A − Change in NWC**

### Cash flow from investing

Forecast investing cash flow is driven primarily by:

**CFI = − Capex**

### Cash flow from financing

Financing cash flow includes:

-   Debt raised
-   Dividends paid

The model then calculates:

**Net Change in Cash = CFO + CFI + CFF**

**Ending Cash = Beginning Cash + Net Change in Cash**

Ending cash feeds back into the balance sheet.

------------------------------------------------------------------------

## 10. DCF valuation

The DCF uses FCFF rather than FCFE.

The calculation is:

**EBIT**\
− **Tax on EBIT**\
= **NOPAT**\
+ **D&A**\
− **Capex**\
− **Change in NWC**\
= **FCFF**

FCFF is discounted using WACC.

The terminal value uses the perpetual-growth method:

**Terminal Value = FY29 FCFF × (1 + g) / (WACC − g)**

Enterprise value is:

**PV of forecast FCFF + PV of terminal value**

Equity value is then:

**Enterprise Value − Net Debt**

Finally:

**Implied Value per Share = Equity Value / Shares Outstanding**

------------------------------------------------------------------------

## 11. WACC

WACC is constructed using a standard capital asset pricing framework.

### Cost of equity

**Cost of Equity = Risk-free Rate + Beta × Equity Risk Premium**

### After-tax cost of debt

**After-tax Cost of Debt = Pre-tax Cost of Debt × (1 − Tax Rate)**

### WACC

**WACC = Equity Weight × Cost of Equity + Debt Weight × After-tax Cost
of Debt**

The model uses:

-   Risk-free rate: 7.02%
-   Equity risk premium: 7.08%
-   Beta: 1.22
-   Pre-tax cost of debt: 7.50%
-   Tax rate: 25%

These inputs result in a model WACC of approximately 15.0%.

------------------------------------------------------------------------

## 12. Sensitivity analysis

The DCF is tested across a matrix of:

-   WACC: 13%--17%
-   Terminal growth: 2.0%--3.5%

This demonstrates how sensitive the implied equity value is to the two
most important DCF assumptions.

The base case is:

**15.0% WACC / 3.0% terminal growth**

------------------------------------------------------------------------

## 13. Model QA

The model contains automated checks covering:

-   Balance-sheet reconciliation
-   Cash-flow reconciliation
-   PP&E roll-forward
-   Debt roll-forward
-   Working-capital linkage
-   Overall model status

The final model currently returns:

**MODEL OK**

The QA framework is intended to catch broken links, inconsistent
roll-forwards and statement integration errors before the model is used
for valuation analysis.

------------------------------------------------------------------------

## 14. Key model limitations

This is a practical v1 model and intentionally contains simplifications.

### Consolidated revenue proxy

India grey cement volume and realisation are used as operating proxies
for consolidated revenue growth. They are not a complete representation
of UltraTech's consolidated revenue mix.

### Simplified depreciation

D&A is based on opening net PP&E rather than a detailed asset-vintage
schedule.

### Simplified working capital

Working-capital ratios are model assumptions and do not attempt to
forecast every balance-sheet component independently.

### Simplified debt schedule

Debt issuance is modelled as an annual assumption rather than a detailed
debt maturity/refinancing schedule.

### No detailed acquisition model

Acquisition accounting, purchase-price allocation and acquired-asset
roll-forwards are outside the scope of this v1 model.

### No quarterly model

The model is annual and does not attempt to capture quarterly
seasonality.

### DCF sensitivity

DCF outputs are highly sensitive to WACC and terminal growth. The
implied value per share should therefore be interpreted as a scenario
output, not as a precise estimate of intrinsic value.

------------------------------------------------------------------------

## 15. Interpretation

The model should be read as a structured analytical framework rather
than a prediction of UltraTech's actual future financial statements.

The most important valuation drivers are:

1.  Cement volume growth
2.  Realisation growth
3.  EBITDA per tonne
4.  Capital expenditure
5.  Working-capital requirements
6.  Cost of capital
7.  Terminal growth

These drivers should be stress-tested before drawing an investment
conclusion.

------------------------------------------------------------------------

## 16. Source hierarchy

Where possible, the model prioritises:

1.  Statutory financial statements and company filings
2.  UltraTech annual reports
3.  UltraTech investor presentations
4.  UltraTech earnings-call materials
5.  Market/reference data for valuation inputs

Source references are maintained separately in the workbook's
`11_Sources` sheet.
