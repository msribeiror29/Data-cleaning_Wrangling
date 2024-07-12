# Data-cleaning_Wrangling.

Prepare dataset for data modeling. 

Apply data cleaning and data wrangling knowledge to structure a database for modeling.

Context: 
An e-commerce company has hired you to collect recency, frequency, and average ticket (RFM) indicators for its customers. RFM stands for:

      R (Recency): Time since the customer made the last purchase (in days)
      F (Frequency): Number of purchases made by the customer
      M (Monetary): Value of the average ticket spent by the customer, where average ticket = average of the total spent per order for each customer.

To achieve this, you will receive a database (CSV file) and will need to create a Python code that produces a CSV output containing only the customer identification and RFM metrics.

About the data:

The table contains information on e-commerce purchases in 37 countries, including customer identification and purchase data.

Coluna	                    Descrição
CustomerID	          Customer identification code
Description	          Product description
InvoiceNo	            Invoice code
StockCode	            Product stock code
Quantity	            Product quantity
InvoiceDate	          Invoice (purchase) date
UnitPrice	            Product unit price
Country	              Country of purchase

How to start?

      1. Import the dataset into Colab.
      2. Understand the data.
      3. Handle missing data.
      4. Handle outliers.

Develop the algorithm to receive the input CSV file and return an output algorithm with the following columns:

      * CustomerID: Customer code.
      * R: Recency.
      * F: Frequency.
      * M: Average ticket.

Development Stages.

To assist you with this process, let's outline the steps.

Step 01: Read the file and inspect the data.

Research the market to identify existing products and their unique features. It's crucial to identify both direct and indirect competitors and emphasize their strengths and points of differentiation.

      	1. Read the dataset.
      	2. Use describe to check the data distribution.
      	3. Analyze the data types.

Stage 02: Missing values in customer identification.

Tip: If present, remove these observations.

        1. Check for null values using isna() and use the sum function to count the number of nulls.
        2. Use the dropna() function to remove the nulls.

Step 3: Unit prices and quantity of products should be equal to or greater than 0.

Tip: If they are less than or equal to 0, remove these entries. 

        1. Check for null data or values less than zero in the price column and remove them if found.
        2. Filter the dataset to only include prices that are above zero. 
        3. Check for null or values less than zero in the quantity column and remove them if found.
        4. Filter the dataset to only include quantities that are above zero.


Step 04: Check for duplicate lines.

   Tip: If duplicate lines are found, remove them as it doesn't make sense to make the same purchase for the same customer at the same time with the same values.

         1. Use the duplicated function to check for duplicate lines.
         2. Remove the duplicate lines.

Step 05: Column data types.

         Tip:
         1. Correct the CustomerID data type.
         2. Correct the InvoiceDate data type.

Coluna	             Tipo esperado
InvoiceNo	            object / str
StockCode	            object / str
Description	          object / str
Quantity	                 int
InvoiceDate	            datetime
UnitPrice	                float
CustomerID	              int
Country	              object / str


Step 06: Handling Outliers.

Tip: Identify and remove extreme outliers where item quantity at purchase is greater than 10,000 and unit price is greater than 5,000.

Step 07: Create an additional column by using the Quantity and UnitPrice columns to calculate the total purchase price.

Step 08: Determine last date.

Tip: Use the max() function. Calculate the date of the last purchase in the dataset as a whole, as we will use this value as a comparison date to calculate recency.

Step 09: Creating Graphs.

        1. Top 10 countries with the highest sales values.
        2. Top 10 best-selling products.
        3. Total sales value per month.
        4. Total sales value per month and country (top 10 only).

Step 10: RFM Calculation.

Tip: Group the data by customer and order/purchase (InvoiceNo) to obtain the date and total price of the order. Then group by the customer and calculate the RFM as follows:

      - R (Recency) is the difference in days between the customer's last purchase and the last purchase available in the dataset.
      - F (Frequency) is the total number of purchases made by the customer.
      - M (Monetary) is the average amount spent by the customer.
