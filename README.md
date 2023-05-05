# Mojo Analysis

## Exploring the Data 

### Costing Summary / Analysis
If you were to choose the all natural route it is going to cost you in the long run:

- Year 2020 it was 36% difference costing around $224 more in dollars. (for naturals)

- Year 2021 it was 66% difference costing around $474 more in dollars. (for naturals)

- Year 2022 it was 59% difference costing around $466 more in dollars. (for naturals)


### Churned Vs Retained Costing Analysis
Going into this I figured that the cost per spray and sum would be different for the retained versus the churned customers but I found out:

Churned:

- The average churned customer spent around 96 per spray summing up to 1162 for the season in dollars for naturals
- The average churned customer spend around 87 per spray summing up to 701 for the season in dollars for synthetic

Retained:

- The average retained customer spent around 104 per spray summing up to 1257 for the season in dollars for naturals
- The average retained customer spend around 98 per spray summing up to 790 for the season in dollars for synthetic

People that go with the natural program churn on average at around 26% compared to 15% churning at a 51% greater rate

![image](https://user-images.githubusercontent.com/94020684/235325730-3a040747-342e-4870-9371-f7b747caa7bb.png)

### Production Analysis

On average a spray tech makes around $20 per hour. WIth that number we esitimated the amount of return you get per minute depending on the amount billed and the duration of time an employee spends at a property. We found out that on average the comapny will be profiting 4.5 dollars per minute on any given property. Here we have a splot of all the unique squarefottages that we cover. You can see the 7500 sqft gives us the worst margins. I did do an anaomly detection on this data so I will assusme that 175K sqft properties consisted of some innaccuracte data due to human error.

![image](https://user-images.githubusercontent.com/94020684/235325711-4e04ea57-ab17-4a14-aa65-a8e19c42996c.png)

```` python

SELECT 
  YEAR(scheduledate) AS Year, 
  SUM(SumOfbillamount) AS TotalRevenue,
  100 * (SUM(SumOfbillamount) - LAG(SUM(SumOfbillamount)) OVER (ORDER BY YEAR(scheduledate))) / LAG(SUM(SumOfbillamount)) OVER (ORDER BY YEAR(scheduledate)) AS company_growth
FROM mosquito_joe.work_orders
GROUP BY YEAR(scheduledate);

````

After year one the company growth was 904.51% then for 2021 to 2022 Mojo experience a 81% growth in revenue 


![image](https://user-images.githubusercontent.com/94020684/235325715-3599fa69-d053-4f40-bf08-f1c5b2ac1a9e.png)
