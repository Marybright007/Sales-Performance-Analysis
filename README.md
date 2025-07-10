# Sales-Performance-Analysis
I utilized SQL to extract and analyze sales data for a motorcycle parts company, calculating net revenue by product line and aggregating the results by month and warehouse. The output was organized by wholesale values for clearer insight. Additionally, I developed visualizations to effectively present trends and key performance indicators derived from the analysis.


**CODE**
SELECT product_line,
    CASE WHEN EXTRACT('month' from date) = 6 THEN 'June'
        WHEN EXTRACT('month' from date) = 7 THEN 'July'
        WHEN EXTRACT('month' from date) = 8 THEN 'August'
    END as month,
    warehouse,
	SUM(total) - SUM(payment_fee) AS net_revenue
FROM sales
WHERE client_type = 'Wholesale'
GROUP BY product_line, warehouse, month
ORDER BY product_line, month, net_revenue DESC
