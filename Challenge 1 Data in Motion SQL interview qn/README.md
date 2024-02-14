## Ace Your Data Analyst Interview Challenge held by <a href='https://www.linkedin.com/company/data-in-motion-llc/'>Data In Motion</a>.
<br>
On Day 2, an E-commerce Case Study is given with the following questions:<br>
<br>

1. Calculate the total order value with a join between Orders and OrderDetails, aggregated by OrderID, then find orders in the top 10%.
2. Calculate the cumulative revenue by month for the year 2022. Sum up the revenue from the start of the year up to the current month, inclusive.
3. Rank customers based on their total spending, highest to lowest, within the year 2022.
4. Calculate the average number of days between orders for each customer. Display the customer name and the average days between orders. For customers with only one order, treat the average days as null. Sort the results by the customer name.
5. Categorize customers into loyalty tiers based on their total spending. Customers who have spent more than $500 are categorized as "Gold," those who have spent between $200 and $500 are categorized as "Silver," and those who have spent less than $200 are categorized as "Bronze." List the customer name, total spending, and their respective loyalty tier.

Here are my solutions based in `Postgresql`.
***

1. Calculate the total order value with a join between Orders and OrderDetails, aggregated by OrderID, then find orders in the top 10%.<br> _Note: Postgresql did not have a TOP % query function_

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/82ce1376-cfdd-45c2-8a23-b3d1bf6637a4)

<br>
2. Calculate the cumulative revenue by month for the year 2022. Sum up the revenue from the start of the year up to the current month, inclusive.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/1ae3a61c-54a1-4d60-bb14-bb994c2d3bb0)

<br>
3. Rank customers based on their total spending, highest to lowest, within the year 2022.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/e4dda413-2cbf-4ebd-8d17-a8a2e8ede12a)

<br>
4. Calculate the average number of days between orders for each customer. Display the customer name and the average days between orders. For customers with only one order, treat the average days as null. Sort the results by the customer name.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/e5d61c63-304c-4c72-a7fe-9e7a9e292faf)

<br>
5. Categorize customers into loyalty tiers based on their total spending. Customers who have spent more than $500 are categorized as "Gold," those who have spent between $200 and $500 are categorized as "Silver," and those who have spent less than $200 are categorized as "Bronze." List the customer name, total spending, and their respective loyalty tier.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/cdccd04d-2710-4d01-9699-d5f2659739f6)

