![[Week 03 - FINA 361H & RAIK 381H - Chapter 5 (Part 1).pdf]]

## Time Value of Money
![[Pasted image 20250204153711.png]]

<mark style="background: #ADCCFFA6;">Discounting</mark> means counting the present value of future cash flows for some reason

![[Pasted image 20250204154243.png]]
<mark style="background: #BBFABBA6;">You enter cash outflows as negative numbers. Any time cash leaves your wallet this is an outflow</mark>
<mark style="background: #BBFABBA6;">You enter cash inflows as positive numbers. Any time cash enters your wallet this is an inflow</mark>

nper() = n, rate() = i/y, pv() = pv, pmt() = pmt, fv() = fv on excel

## Actual Explanations
<mark style="background: #ADCCFFA6;">Present Value (PV)</mark> Present value is the current worth of a future sum of money or cash flow, discounted at a specific rate of return (discount rate). It answers the question: _What is the value today of a future amount of money?_
![[Pasted image 20250207121149.png]]

<mark style="background: #ADCCFFA6;">Payment (PMT)</mark> PMT refers to a series of equal, periodic payments or receipts (e.g., loan payments, annuities, or savings contributions). It is a key component in calculating the present or future value of an annuity (a series of cash flows)
![[Pasted image 20250207121732.png]]

<mark style="background: #ADCCFFA6;">Future Value (FV)</mark> Future value is the value of a current sum of money or cash flow at a specified date in the future, based on an assumed rate of growth (interest rate). It answers the question: _What will this amount of money be worth in the future?_
![[Pasted image 20250207121932.png]]

1. **Present Value (PV)** and **Future Value (FV)** are linked through the time value of money. PV is the discounted value of a future amount, while FV is the compounded value of a present amount.
2. **Payment (PMT)** is used when dealing with a series of cash flows (e.g., annuities). It can be used to calculate either the present value or future value of those cash flows.

The <mark style="background: #ADCCFFA6;">Effective Annual Rate (EAR)</mark> converts the interest rate into an effective annual rate (with single compounding). Used to compare interest rates in different periods so you can see which one is better
$$EAR=(1+\frac{Rate}{Periods})^{Periods}-1$$
Note: the periods are specifically periods PER YEAR since we're putting it all in year form