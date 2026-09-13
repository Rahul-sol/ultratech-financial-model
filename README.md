# UltraTech Cement --- Financial Modelling & DCF Analysis

A practical, interview-defensible financial modelling project built
around **UltraTech Cement Limited**, covering historical financials,
driver-based forecasting, integrated three-statement modelling,
supporting schedules and DCF valuation.

> **Disclaimer:** This is an independent learning/portfolio project. It
> is not investment advice, a reproduction of UltraTech's internal
> model, or professional sell-side research.

------------------------------------------------------------------------

## Project objective

The objective was to build an end-to-end company financial model from
publicly available company disclosures while understanding the logic
behind each major component.

The project demonstrates:

-   Historical financial statement collection and standardisation
-   Operating-driver based forecasting
-   Integrated Income Statement, Balance Sheet and Cash Flow Statement
-   Working-capital modelling
-   PP&E and capex schedule
-   Debt and interest schedule
-   FCFF-based DCF valuation
-   WACC construction
-   DCF sensitivity analysis
-   Automated model QA checks
-   Documentation of assumptions, sources and limitations

The emphasis is on **understanding and defensibility rather than model
complexity**.

------------------------------------------------------------------------

## Model architecture

``` text
Company filings / public disclosures
                ↓
        Historical financials
                ↓
          Operating drivers
                ↓
        ┌───────────────────┐
        │ Forecast IS       │
        │ Forecast BS       │
        │ Forecast CFS      │
        └───────────────────┘
                ↕
        Supporting schedules
        • Working capital
        • PP&E / capex
        • D&A
        • Debt / interest
                ↓
              FCFF
                ↓
              DCF
                ↓
       Sensitivity analysis
                ↓
           QA / validation
```

------------------------------------------------------------------------

## Workbook structure

  Sheet                   Purpose
  ----------------------- -------------------------------------------------------
  `01_Cover`              Project overview, model scope and legend
  `02_Historicals`        FY24A--FY26A historical P&L
  `03_Drivers`            Operating assumptions and forecast drivers
  `04_Income_Statement`   Historical and forecast income statement
  `05_Balance_Sheet`      Historical and forecast balance sheet
  `06_Cash_Flow`          Forecast cash flow statement
  `07_Schedules`          PP&E, D&A, debt, interest and working capital
  `08_DCF`                FCFF, WACC and DCF valuation
  `09_Sensitivity`        WACC / terminal-growth sensitivity
  `10_Checks`             Automated model QA
  `11_Sources`            Historical sources and assumption references
  `Mini_Model`            Learning appendix demonstrating basic model mechanics

------------------------------------------------------------------------

## Historical period

**FY24A--FY26A**

The historical model uses consolidated financial information from
UltraTech's statutory disclosures, annual reports and investor
materials.

A specific focus was placed on reporting-definition consistency. The
historical revenue series uses **statutory Revenue from Operations**
rather than mixing it with management's separately presented Net Sales
definition.

FY24 comparatives were also treated carefully because of the Kesoram
transaction and resulting restatement.

------------------------------------------------------------------------

## Forecast period

**FY27E--FY29E**

The forecast uses operating drivers rather than simply applying
arbitrary percentage growth to financial outputs.

### Key operating drivers

-   India grey cement capacity
-   Capacity utilisation
-   Production
-   Sales volume
-   Blended realisation per tonne
-   EBITDA per tonne

### Core forecasting logic

**Revenue**

Revenue growth is anchored to FY26 consolidated revenue and uses India
grey cement volume and realisation as operating proxies.

**Operating EBITDA**

``` text
Sales volume × EBITDA / tonne
```

**PP&E**

``` text
Closing PP&E = Opening PP&E + Capex − D&A
```

**Working capital**

``` text
NWC = AR + Inventory − AP
```

**Cash flow**

``` text
CFO = PAT + D&A − Change in NWC
```

**FCFF**

``` text
FCFF = EBIT × (1 − Tax Rate)
     + D&A
     − Capex
     − Change in NWC
```

------------------------------------------------------------------------

## DCF valuation

The DCF uses a standard FCFF framework.

### WACC

Cost of equity is calculated using CAPM:

``` text
Cost of Equity = Risk-free Rate + Beta × Equity Risk Premium
```

WACC then combines the cost of equity and after-tax cost of debt using
the modelled capital structure.

### Base-case assumptions

  Input                    Base case
  ---------------------- -----------
  Risk-free rate               7.02%
  Equity risk premium          7.08%
  Beta                          1.22
  Pre-tax cost of debt         7.50%
  Tax rate                       25%
  WACC                       \~15.0%
  Terminal growth               3.0%

### Base-case output

  Metric                    Model output
  ----------------------- --------------
  FY27E FCFF                 \~₹6,553 cr
  FY28E FCFF                 \~₹8,170 cr
  FY29E FCFF                \~₹10,169 cr
  Enterprise Value          \~₹75,965 cr
  Less: Net Debt            \~₹22,426 cr
  Equity Value              \~₹53,539 cr
  Implied value / share     **\~₹1,817**

The implied value is a model output and should not be interpreted as a
precise intrinsic value or investment recommendation.

------------------------------------------------------------------------

## Sensitivity analysis

The DCF is tested across:

-   **WACC:** 13%--17%
-   **Terminal growth:** 2.0%--3.5%

Base case:

**15.0% WACC / 3.0% terminal growth → \~₹1,817/share**

The sensitivity analysis is included because DCF valuation is
particularly sensitive to the discount rate and terminal-growth
assumption.

------------------------------------------------------------------------

## Model QA

The workbook includes automated checks for:

-   Balance-sheet reconciliation
-   Cash-flow reconciliation
-   PP&E roll-forward
-   Debt roll-forward
-   Working-capital linkage
-   Overall model status

Final model status:

**MODEL OK**

The purpose of these checks is to identify broken links, inconsistent
roll-forwards and statement integration errors before interpreting the
valuation output.

------------------------------------------------------------------------

## Key modelling judgements

This project intentionally uses a practical level of complexity.

### Consolidated revenue proxy

India grey cement volume and blended realisation are used as operating
proxies for consolidated revenue growth. They are not a complete
representation of UltraTech's consolidated revenue mix.

### Simplified depreciation

Forecast D&A is based on opening net PP&E rather than a detailed
asset-vintage depreciation schedule.

### Simplified working capital

Forecast working capital uses selected revenue/cost ratios rather than
modelling every individual current-asset and current-liability
component.

### Simplified debt schedule

Debt issuance is modelled as an annual assumption rather than a detailed
maturity/refinancing schedule.

### No detailed acquisition model

Acquisition accounting and purchase-price allocation are outside the
scope of this v1 model.

These choices were deliberate: the goal was to demonstrate **integrated
modelling logic and valuation mechanics without overbuilding the
model**.

------------------------------------------------------------------------

## What this project demonstrates

The project is intended to demonstrate the ability to move from:

**Public filings → historical data → business drivers → financial
forecasts → integrated statements → supporting schedules → FCFF → DCF →
sensitivity → QA**

It also demonstrates an understanding of the distinction between:

-   Source data
-   Model assumptions
-   Formula-driven outputs
-   Analyst judgement
-   Simplifying conventions

------------------------------------------------------------------------

## Repository structure

``` text
financial-modelling-company-case/
│
├── README.md
│
├── model/
│   └── Company_Financial_Model.xlsx
│
├── data/
│   ├── historical_data.xlsx
│   └── sources.md
│
├── documentation/
│   ├── methodology.md
│   └── assumptions.md
│
├── screenshots/
│   ├── historicals.png
│   ├── forecast.png
│   ├── three_statement.png
│   ├── dcf.png
│   └── sensitivity.png
│
├── LICENSE
└── DISCLAIMER
```

------------------------------------------------------------------------

## Documentation

-   `documentation/methodology.md` --- explains the modelling framework
    and calculation methodology.
-   `documentation/assumptions.md` --- lists key operating, financial
    and valuation assumptions.
-   `data/sources.md` --- intended source register for historical and
    market/reference inputs.

------------------------------------------------------------------------

## Data sources

Primary sources include UltraTech Cement's:

-   Annual reports
-   Audited financial results
-   Investor presentations
-   Earnings-call materials
-   Official financial disclosures

Market/reference inputs for the DCF are separately documented in the
workbook's `11_Sources` sheet.

------------------------------------------------------------------------

## Limitations

This model should not be interpreted as:

-   UltraTech management guidance
-   An internal company planning model
-   Professional sell-side research
-   A complete investment recommendation
-   A substitute for detailed due diligence

Forecast assumptions are independent modelling assumptions and may
differ materially from actual future results.

------------------------------------------------------------------------

## Author

**Rahul Solanki**

Finance / financial data research professional building practical skills
in financial modelling, equity research and quantitative financial
analysis.
