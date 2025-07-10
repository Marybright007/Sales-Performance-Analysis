# Sales-Performance-Analysis
I utilized SQL to extract and analyze sales data for a motorcycle parts company, calculating net revenue by product line and aggregating the results by month and warehouse. The output was organized by wholesale values for clearer insight. Additionally, I developed visualizations to effectively present trends and key performance indicators derived from the analysis.


**SQL QUERY** <br>

```SELECT  product_line, <br>
 CASE WHEN EXTRACT('month' from date) = 6 THEN 'June' <br>
          WHEN EXTRACT('month' from date) = 7 THEN 'July' <br>
          WHEN EXTRACT('month' from date) = 8 THEN 'August' <br>
          END as month, <br>
          warehouse, <br>
	  SUM(total) - SUM(payment_fee) AS net_revenue <br> 
FROM sales <br>
WHERE client_type = 'Wholesale' <br>
GROUP BY product_line, warehouse, month <br>
ORDER BY product_line, month, net_revenue DESC <br>
