# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql
SELECT 
    MIN(price_per_sqm) AS MinPricePerSqm,
    MAX(price_per_sqm) AS MaxPricePerSqm
FROM 
    flats;
```

### Question 2

Select the average price per sqm for flats in each town.

```sql
SELECT 
    town,
    ROUND(AVG(price_per_sqm), 2) AS AvgPricePerSqm
FROM 
    flats
GROUP BY 
    town;
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
        WHEN price < 400000 THEN 'Budget'
        WHEN price BETWEEN 400000 AND 700000 THEN 'Mid-Range'
        ELSE 'Premium'
    END AS PriceCategory,
    COUNT(*) AS FlatCount
FROM 
    flats
GROUP BY 
    PriceCategory
ORDER BY 
    FlatCount DESC;
```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql
SELECT 
    town,
    COUNT(*) AS FlatsSold
FROM 
    flats
WHERE 
    sale_date BETWEEN '2017-01-01' AND '2017-03-31'
GROUP BY 
    town
ORDER BY 
    FlatsSold DESC;
```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
