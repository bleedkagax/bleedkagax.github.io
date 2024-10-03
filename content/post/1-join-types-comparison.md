---
title: Join Types Comparison
name: 1-join-types-comparison
date: 2024-09-07
draft: false
tags:
  - Mysql
share: "true"
---

# Input Tables

![|400*400](/img/1-join-types-comparison.png)

# INNER JOIN 

INNER JOIN returns only the rows where there's a match between both tables based on the join condition.

```sql
SELECT A.ID, A.Name, B.ID, B.Department
FROM A
INNER JOIN B ON A.ID = B.ID  
```

![|400*400](/img/1-join-types-comparison-1.png)

# LEFT JOIN

LEFT JOIN returns all rows from the left table (A), and the matched rows from the right table (B). If there's no match, NULL values are used for the right table columns.

```sql
SELECT A.ID, A.Name, B.ID, B.Department
FROM A
LEFT JOIN B ON A.ID = B.ID  
```

![400*400](/img/1-join-types-comparison-2.png)
# RIGHT JOIN

RIGHT JOIN returns all rows from the right table (B), and the matched rows from the left table (A). If there's no match, NULL values are used for the left table columns.

```sql
SELECT A.ID, A.Name, B.ID, B.Department  
FROM A  
RIGHT JOIN B ON A.ID = B.ID
```

![400*400](/img/1-join-types-comparison-3.png)

# FULL JOIN

FULL JOIN returns all rows from both tables, matching rows where possible and using NULL values where there is no match.

Note: MySQL doesn't directly support FULL JOIN, but it can be simulated using a combination of LEFT JOIN, UNION, and RIGHT JOIN:

```sql
SELECT A.ID, A.Name, B.ID, B.Department  
FROM A  
LEFT JOIN B ON A.ID = B.ID  
UNION  
SELECT A.ID, A.Name, B.ID, B.Department  
FROM B  
LEFT JOIN A ON A.ID = B.ID  
WHERE A.ID IS NULL
```


![400*400](/img/1-join-types-comparison-4.png)

# CROSS JOIN

CROSS JOIN returns the Cartesian product of both tables, combining each row from the first table with every row from the second table.

```sql
SELECT A.ID, A.Name, B.ID, B.Department  
FROM A  
CROSS JOIN B
```

![400*400](/img/1-join-types-comparison-5.png)