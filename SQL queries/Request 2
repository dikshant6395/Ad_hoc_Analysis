/*2. What is the percentage of unique product increase in 2021 vs. 2020? The
final output contains these fields,
unique_products_2020
unique_products_2021
percentage_chg*/

WITH cte1 AS (
    SELECT COUNT(DISTINCT p.product_code) AS unique_products_2020
    FROM dim_product p
    JOIN fact_sales_monthly s
    ON p.product_code = s.product_code
    WHERE s.fiscal_year = '2020'
    GROUP BY s.fiscal_year
),
cte2 AS (
    SELECT COUNT(DISTINCT p.product_code) AS unique_products_2021
    FROM dim_product p
    JOIN fact_sales_monthly s
    ON p.product_code = s.product_code
    WHERE s.fiscal_year = '2021'
    GROUP BY s.fiscal_year
)
SELECT 
    cte1.unique_products_2020,
    cte2.unique_products_2021,
    (cte2.unique_products_2021 - cte1.unique_products_2020) * 100.0 / cte1.unique_products_2020 AS percentage_chg
FROM cte1
CROSS JOIN cte2;
