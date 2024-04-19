# rdtfgycgvhghvf
transaction_id,customer_id,product_id,transaction_date,amount
1,101,1,2024-04-01,50.00
2,102,2,2024-04-01,30.00
3,103,3,2024-04-02,25.00
4,101,4,2024-04-03,40.00
5,102,1,2024-04-03,50.00
6,104,2,2024-04-04,30.00
7,101,3,2024-04-05,25.00
8,103,4,2024-04-06,40.00
9,105,1,2024-04-06,50.00
10,102,3,2024-04-07,25.00

SELECT 
    SUBSTR(transaction_date, 1, 7) AS month,
    SUM(quantity) AS total_quantity_sold
FROM 
    your_table_name
GROUP BY 
    SUBSTR(transaction_date, 1, 7);



SELECT 
    customer_id
FROM 
    your_table_name
GROUP BY 
    customer_id
HAVING 
    COUNT(DISTINCT product_id) >= 2;


SELECT 
    customer_id,
    SUM(amount) AS total_amount_spent
FROM 
    your_table_name
GROUP BY 
    customer_id
ORDER BY 
    total_amount_spent DESC
LIMIT 3;


student_id,student_name,subject,score
1,John,Math,90
2,Alice,Math,85
3,Bob,Math,92
4,Emily,Math,88
5,John,Science,85
6,Alice,Science,90
7,Bob,Science,88
8,Emily,Science,92
9,John,English,80
10,Alice,English,75
11,Bob,English,78
12,Emily,English,85

SELECT 
    student_id,
    student_name,
    AVG(score) AS average_score
FROM 
    your_table_name
GROUP BY 
    student_id,
    student_name;

