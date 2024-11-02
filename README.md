## SQL Problem Solved
Welcome to my repository dedicated to solving SQL problems sourced from LeetCode and other platforms. This project showcases my skills in database management and query optimization through a collection of diverse SQL challenges.

### About This Repository
In this repository, you'll find well-documented solutions to various SQL problems, demonstrating my ability to write efficient queries and solve complex data manipulation tasks. Each problem is accompanied by explanations and insights into the thought process behind the solution, making it a valuable resource for both learning and reference.

### Why SQL?
SQL is a fundamental skill in data analysis, back-end development, and many other fields. By tackling these problems, I aim to deepen my understanding of SQL concepts and improve my problem-solving abilities. This repository is not just a showcase of my work; it's also a way for me to continuously learn and grow in the realm of data management.

#### Lets Start......................

### Platform: Leetcode, Difficulty:Medium
#### Q1:If the customer's preferred delivery date is the same as the order date, then the order is called immediate; otherwise, it is called scheduled.The first order of a customer is the order with the earliest order date that the customer made. It is guaranteed that a customer has precisely one first order.Write a solution to find the percentage of immediate orders in the first orders of all customers, rounded to 2 decimal places.

```sql
WITH cte AS (
    SELECT
        customer_id,
        MIN(order_date) AS first_order_date
    FROM
        Delivery
    GROUP BY
        customer_id
)

SELECT
    ROUND(
        SUM(CASE WHEN d.order_date = d.customer_pref_delivery_date THEN 1 ELSE 0 END) / 
        NULLIF(COUNT(*), 0) * 100, 
        2
    ) AS immediate_percentage
FROM
    cte ct
JOIN
    Delivery d ON ct.customer_id = d.customer_id AND ct.first_order_date = d.order_date;
```

### Platform: Leetcode, Difficulty: Eassy
#### Q1:Write a solution that will, for each user, return the number of followers.Return the result table ordered by user_id in ascending order.
```sql
select
   user_id,
   count(follower_id) as  followers_count
from Followers
group by user_id
order by user_id asc;
```

### Platform: Leetcode, Difficulty: Eassy
#### Q1:Write a solution to find all the classes that have at least five students.Return the result table ordered by user_id in ascending order.
```sql
select
   class
from Courses
group by class
having count(student)>=5
```

