# Chapter 11: Capital Budgeting Basics

## Net Present Value (NPV)
- Gives us the value of a project in today’s dollars after accounting for borrowing costs and the riskiness of the project (both of which would be captured in the discount rate).
- Accept project when:
  - NPV > 0.
- If we have limited capital to invest, we choose the project with the higher NPV.
- Crossover rate of two projects is the discount rate at which the NPV of the two projects intersect.
- How to implement:
  - `NPV()` function in Excel, but don’t forget to put t=0 cash flows outside of the function!!!

## Internal Rate of Return (IRR)
- The discount rate which makes our NPV zero. In other words, the rate of return produced by the project.
- Accept project when:
  - IRR > WACC (or project’s discount rate if different from WACC).
- Pitfalls:
  - Multiple IRRs with non-normal cash flows:
    - **Normal Cash Flows**: - - - + + + + + ...
    - **Non-Normal Cash Flows**: - - - + + + + + - - -
  - Assumes capital can be reinvested at IRR.
    - A better assumption is that it can be reinvested at WACC.
  - How to choose between mutually exclusive projects?
    - IRR does not help us here. NPV does.
- How to implement:
  - `IRR()` function in Excel.

## Modified Internal Rate of Return (MIRR)
- Solves two of the IRR problems:
  - Multiple IRRs.
  - Reinvestment at IRR assumption.
- Procedure:
  - Compute FV of all inflows at the last time period (assumes reinvestment at WACC).
  - Compute IRR like before.
  - Accept project when MIRR > WACC (or project’s discount rate if different from WACC).
- How to implement:
  - `MIRR()` function in Excel, where the WACC is both the finance and reinvestment rate.

## Regular Payback Period
- Tells us how many years to break even on a project.
- Accept project when:
  - ????? No clear rule.
- Pitfalls:
  - Tells us nothing about cash flows after break-even.
  - Ignores time value of money (TVM).
  - Does not accurately help us decide between two projects.
- How to implement:
  - Calculate cumulative cash flows and determine when the project recoups its initial investment. No Excel formula that I’m aware of.

## Discounted Payback Period
- Tells us how many years to break even on a project, after properly accounting for the time value of money.
- Accept project when:
  - ????? No clear rule.
- Pitfalls:
  - Tells us nothing about cash flows after break-even.
  - Ignores time value of money (TVM).
  - Does not accurately help us decide between two projects.
- How to implement:
  - Calculate cumulative discounted cash flows and determine when the project recoups its initial investment. No Excel formula that I’m aware of.

**Big picture ideas from Chapter 11**: NPV is best, but you should be familiar with the others.

# Chapter 12: More Capital Budgeting

- Basically, we’re doing a bunch of NPVs in this chapter.
  - Don’t forget to exclude the t=0 cash flows from the `NPV()` function!!!
- We discussed depreciation:
  - Straight line vs MACRS.
  - After-tax salvage value:
    - Book value today = Original price – accumulated depreciation.
    - Gain on sale = Sales price – book value.
    - Taxes on gain = Tax rate * gain on sale.
    - After-tax salvage value = Sales price – Taxes on gain.

## Free Cash Flow
- **FCF** = EBIT*(1- τ) + depreciation - CAPEX - increase in NOWC.
  - **Incremental FCF** = Incremental EBIT*(1- τ) + Incremental depreciation - Incremental CAPEX - Incremental increase in NOWC.
- **EBIT**:
  - Think of Income Statement:
    - Incremental Earnings.
    - - Incremental Operating Expenses (excluding depreciation).
    - = Incremental EBITDA.
    - - Incremental Depreciation <===== don’t forget to include!!!!
    - = Incremental EBIT.
- **Depreciation**:
  - Incremental depreciation = new depreciation – old depreciation.
- **CAPEX**:
  - Put purchase price of new equipment here (including installation fees).
  - Put after-tax salvage value here.
    - After-tax salvage value = sales price – taxes on gain.
    - Taxes on gain = tax rate * (sales price – book value).
  - If you are buying a building, this will hurt your cash flows (as manifest through a reduction in FCF). If you are selling some equipment, this will help your cash flows (as manifest through an increase in FCF).
- **NOWC**:
  - If you buy a new factory or machine, you will need to increase your working capital to do so. In most of these problems, we do so at time 0, which reduces our free cash flows. Think of this as building up our inventory in a new factory. Once the life of the project is finished, we “release the working capital” by using up this inventory, which improves our free cash flows.
- Take NPV of incremental FCF for both New Project Analysis and Replacement Analysis.

# Personal Finance

## Traditional IRA/401k
- Income NOT taxed now (federal & state).
- No taxes on dividends each year.
- Taxed on back end (when you withdraw) => ENTIRE withdrawal amount (@ ordinary income tax rates).
- Invest $1 income:
  - FV = $1*(1+R)^N*(1-τlater).

## Roth IRA/401k
- Income taxed now (federal & state).
- No taxes on dividends each year.
- NOT taxed on back end (when you withdraw).
- Invest $1 income:
  - FV = $1*(1-τnow)*(1+R)^N.

## Roth vs Trad
- Roth if τlater > τnow.
- Trad if τlater < τnow.
  - This will be true for you for most of your career.
- Roth gives you more liquidity, since you can always touch the principal (what you’ve put in). However, you can access liquidity slowly in Trad accounts via “Roth IRA Conversion Ladders” (google it).

## Taxable brokerage account:
- Income taxed now (federal & state).
- Dividends taxed forever, creating a “dividend tax drag” on returns equal to dividend yield * tax rate on dividends.
- Gains taxed down the road:
  - Capital gain = Sales price – purchase price.
  - Capital gains tax = Capital gain * tax rate on capital gains.
- Invest $1 of income:
  - Initial investment amount = $1*(1-τnow).
  - FVafter_tax = $1*(1-τnow)*(1+R-dividend tax drag)^N – cap gains taxes.
  - FVafter_tax = $1*(1-τnow)*(1+R-dividend tax drag)^N – τCapGains *($1*(1-τnow)*(1+R-dividend tax drag)^N -$1*(1-τnow)).

## Tax strategies
- Thinking about Roth vs Trad.
- Prioritize tax-advantaged accounts (401k, IRA, & HSA) over taxable brokerage.
- In taxable brokerage:
  - Tax loss harvest.
  - Low turnover to avoid cap gains taxes; don’t trade!!!
- Relocate to lower tax state in retirement.
- If you have sufficient cash flow AND your employer allows it, take advantage of the “mega backdoor Roth” (Google/ChatGPT it). This could save you hundreds of thousands of dollars in taxes over your lifetime.