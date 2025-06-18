![[Week 09 - FINA 361H & RAIK 381H - Chapter 11.pdf]]



<mark style="background: #ADCCFFA6;">Capital Budgeting</mark> is the process that helps us decide whether it makes sense to pursue a project or not
Different techniques include:
1. Net Present Value (NPV) which is the best one
2. Internal Rate of Return (IRR) which is helpful to know but not better than NPV
3. Modified Internal Rate of Return (MIRR)
4. Regular Payback Period
5. Discounted Payback Period

## Net Present Value
Remember that NPV() takes the cash flows from years 1+, you have to manually add the time 0 cash flows to get the NET present value

NPV tells us, after accounting for our cost of capital (WACC), the present value of predicted earnings of a project
- Accept positive NPVs, reject negative NPVs
- If you have two projects and not enough for both, invest with highest NPV

Some projects are better at some discount rates and others are better for other discount rates. The point at which the NPV is the same is known as the <mark style="background: #ADCCFFA6;">crossover rate</mark>
![[Pasted image 20250408160346.png]]
To find a crossover rate, define a cell for the difference between the two and goal seek to get it to 0

NPV Benefits
- Easy to calculate
- Outcome is easy to interpret
Disadvantages
- None for capital budgeting
## Internal Rate of Return
The <mark style="background: #ADCCFFA6;">Internal Rate of Return</mark> is the discount rate that makes the NPV to equal 0. It calculates the return of each project basically (comparable to the yield of a bond)
- Accept project if IRR  > WACC, reject if IRR < WACC

You would set NPV to 0 and goal seek/solver it
Or, you can use the IRR() function in Excel which will give the same answer

Problems with IRR
1. Non-normal cash flows will produce multiple IRR's
   Normal CF: ---+++++....
   Non-Normal CF: -++++-
2. An assumption of this technique assumes that any cash flows a project generates are IMMEDIATELY reinvested at the IRR back into the project (reinvestment assumption). Most of the time, investing back at the IRR is unrealistic because the investment rate will change
	1. NPV assumes it can be reinvested at the WACC, which is a more realistic assumption
3. When choosing between mutually exclusive projects, the project with a higher IRR doesn't necessarily mean that project has the highest return

Benefits
1. Easy to calculate
2. Outcome is easy to interpret

## Modified Internal Rate of Return
MIRR Benefits:
1. Easy to calculate
2. Outcome is easy to interpret
3. Fixes the multiple IRR's and reinvestment assumption problems with regular IRR
Problems:
4. Mutually exclusive projects are still tricky to decide

For <mark style="background: #ADCCFFA6;">Modified IRR</mark>, you compute the future value of all inflows at last time period (assume reinvestment occurs at WACC), and then compute IRR as before
![[Pasted image 20250408161926.png]]
Where $1,579.50 is the future value of all the cash flows beforehand (except at time 0)

Or, you can just use MIRR(). You put in all the columns and put in the WACC for the other two inputs usually

## Regular Payback Period
The <mark style="background: #ADCCFFA6;">Regular payback period</mark> asks how long it takes for a project to be repaid

1. Compute the cumulative CF for a project
Basically you have an initial investment at time 0. Cumulative CF is just the previous times +/- the current time
![[Pasted image 20250408162649.png]]
Time 1 has a cumulative CF in year 1 of -500 because it's -1,000 + 500
2. You find the year that first produces a positive value, that time is the whole number. To get the decimal points of a year, it's just the previous negative cumulative cash flow over the positive cash flow of the time
   Above, it was -100 cumulatively in year 2, so in year 3 we are finally positive (so 2 years), but to calculate the decimal you do 100/300 to get 1/3, add it to 2 years for 2.333 years 

There is no excel formula that does it for you

Pros:
1. Easy to calculate
2. Easy to interpret (it's just years to break even)
Cons:
3. Ignores the time value of money. It treats CF from all time periods as equal
4. Cash flows beyond payback year are ignored
5. How do you decide what a good payback period is? Is 5 years acceptable? How do you know?

## Discounted Payback Period
The <mark style="background: #ADCCFFA6;">discounted payback period</mark> attempts to fix some of the issues with payback period by discounting cumulative cash flows (usually at the WACC)

Pros
1. Easy to calculate
2. Easy to interpret
3. It does take into account the time value of money
Cons
4. Cash flows beyond payback year are ignored
5. What is a good payback period?

![[Pasted image 20250408163325.png]]
