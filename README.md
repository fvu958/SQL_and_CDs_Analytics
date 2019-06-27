# Business Analytics Using SQL Project

A project using SQL to answer business questions surrounding the operations of a record store. I use subqueries, multiple joins, set operations, aggregate functions, and visualize some of my findings

# Observations:
- The United States accounts for ~22% of sales
- Based on the data provided, the Czech Republic, the UK, and India present opportunities we can explore, but the sample size is small so we should be careful of overcommitting 


# Test
```python
support_rep_sales = '''
    WITH support_rep_sales AS
    (
        SELECT
            c.support_rep_id,
            i.customer_id,
            SUM(i.total) total
        FROM invoice i
        INNER JOIN customer c ON c.customer_id = i.customer_id
        GROUP BY c.support_rep_id, i.customer_id
    )
    
SELECT
    e.first_name || " " || e.last_name employee_name,
    e.hire_date,
    SUM(srs.total) rep_total
    FROM employee e
    INNER JOIN support_rep_sales srs ON e.employee_id = srs.support_rep_id
    GROUP BY employee_name;
'''
```