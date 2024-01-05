# coffee-sales-dashboard
Coffee sales portfolio project - gathering and transforming the data, analysing and visualizing it by creating a dashboard in Excel

First we have checked our database for any duplicates and luckly there wasn’t any.

Now we go to formatting.

We gathered the customer data using the **XLOOKUP** formula and then the traditional **INDEX  and MATCH** formula to gather the product data.

**INDEX MATCH** is a good choice as it’s dynamic and we will be able to populate all of the needed columns. For the **XLOOKUP** we will repeat our formula for each column.
To gather customer name we will use **XLOOKUP** formula:

_=XLOOKUP(C2,customers!$A$1:$A$1001,customers!$B$1:$B$1001,,0)
_
To gather customer email data we will use very similar formula. It just needs modifying so any NULL data (empty cells in the email column) will return a blank cell rather than default “0” value.
_=IF(XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)=0,"",XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0))
_
To populate the country data we will use the same formula as for the names, but we will be looking up a different value:
_=XLOOKUP(C2,customers!A$1:A$1001,customers!$G$1:$G$1001,,0)
_
To gather product data we used INDEX and MATCH formula.

We used two **MATCH** formulas to populate both rows and columns data.

_=INDEX(products!$A$1:$G$49,MATCH(orders!$D2,products!$A$1:$A$49,0),MATCH(orders!I$1,products!$B$1:$G$1,0))
_
We locked in specific columns / rows values to make sure the formula populates correct data.

To calculate the sales we simply multiplied Unit Price column values by the Quantity column values.

We had then formatted both Unit Price and Sales columns to be in GBP figures and the Size column to be showing as ‘kg’ and finally formatted the date to make sure it’s fully readable for all the users and showing as ‘DD-MMM-YYYY.

To make the data more readable and user friendly we changed both Coffee Type and Roast Type to full names rather than the abbreviations. So ‘Rob’ becomes ‘Robusta’, ‘D’ becomes ‘Dark’ and so on. To do that we used the IF formula.

At the end we will add a “Loyalty Card” column at the last column. To populate data we will again use the XLOOKUP formula to see if the Customer ID match to each order has a Loyalty Card assigned to it.

_=XLOOKUP([@[Customer ID]],customers!$A$1:$A$1001,customers!$I$1:$I$1001,,0)
_
Before we start creating our Pivot Tables / Pivot Charts we turn our gathered data into a table to make it easier to manage and manipulate.

First we create a Total Sales table and chart (please see the “total_sales” sheet). 

Then we created a Sales By Country pie chart and Top Customers Bar Chart and formatted everything to nicely fit together.

At the end we copied all our pivot charts to a separate sheet and created a dashboard.

