# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql
SELECT 
	ROUND(MIN(resale_price / floor_area_sqm), 2) AS min_price_per_sqm,
	ROUND(MAX(resale_price / floor_area_sqm), 2) AS max_price_per_sqm
FROM resale_flat_prices_2017;
```

### Question 2

Select the average price per sqm for flats in each town.

```sql
SELECT 
	town,
	ROUND(AVG(resale_price / floor_area_sqm), 2) AS avg_price_per_sqm
FROM resale_flat_prices_2017
GROUP BY 
	town
ORDER BY
	avg_price_per_sqm DESC;
```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```sql
SELECT 
	CASE 
		WHEN resale_price < 400000 THEN 'Budget'
		WHEN resale_price BETWEEN 400000 AND 700000 THEN 'Mid-Range'
		ELSE 'Premium'
	END AS price_range,
	COUNT(*) AS num_of_flats
FROM 
	resale_flat_prices_2017
GROUP BY
	price_range
ORDER BY
	num_of_flats DESC;
```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql
SELECT 
	town,
	COUNT(*) AS num_of_flats_sold
FROM 
	resale_flat_prices_2017
WHERE 
	month IN ('2017-01', '2017-02', '2017-03')
GROUP BY
	town
ORDER BY
	num_of_flats_sold;
```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
