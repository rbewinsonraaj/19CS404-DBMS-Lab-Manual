# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1245" height="518" alt="image" src="https://github.com/user-attachments/assets/1ee74061-96d5-44f2-8c7c-a71c103b0105" />


```sql
SELECT grade, COUNT(*)
FROM customer
WHERE grade > (
    SELECT AVG(grade)
    FROM customer
    WHERE city = 'New York'
)
GROUP BY grade;

```

**Output:**

<img width="584" height="421" alt="image" src="https://github.com/user-attachments/assets/2edc5ec2-6505-49e2-aecb-6535f16e01e8" />


**Question 2**
---
<img width="1002" height="740" alt="image" src="https://github.com/user-attachments/assets/8038cb49-808c-437f-8a9f-6e4c793a8c9d" />


```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);

```

**Output:**

<img width="1155" height="359" alt="image" src="https://github.com/user-attachments/assets/eaabcfc7-dfa0-41c8-8324-5b740cbc8d06" />


**Question 3**
---
<img width="856" height="558" alt="image" src="https://github.com/user-attachments/assets/acbc0897-612b-49c6-bf9c-3bfa0a922182" />



```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';

```

**Output:**

<img width="1144" height="367" alt="image" src="https://github.com/user-attachments/assets/e1b96268-1877-4e23-b27c-36e1c8534b08" />


**Question 4**
---
<img width="1244" height="570" alt="image" src="https://github.com/user-attachments/assets/b22f3f6e-e05b-4bf3-88f5-a16d31ef07d7" />


```sql
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="693" height="451" alt="image" src="https://github.com/user-attachments/assets/bf2049bc-faca-4b51-830a-1780eaa81a0c" />


**Question 5**
---
<img width="1030" height="487" alt="image" src="https://github.com/user-attachments/assets/8d77ea54-26d5-4e69-9666-0332ceaa93a7" />


```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);

```

**Output:**

<img width="527" height="482" alt="image" src="https://github.com/user-attachments/assets/1444ab14-7c04-42fd-9011-f920dfb16a8e" />


**Question 6**
---
<img width="960" height="509" alt="image" src="https://github.com/user-attachments/assets/670af8f2-2708-4902-9313-a57574c286bf" />


```sql
SELECT name
FROM customer
WHERE phone IN (
    SELECT phone
    FROM customer
    GROUP BY phone
    HAVING COUNT(*) = 1
);

```

**Output:**

<img width="448" height="500" alt="image" src="https://github.com/user-attachments/assets/971ba8f4-69b2-4a00-a362-cfc086ea7daa" />


**Question 7**
---
<img width="1186" height="577" alt="image" src="https://github.com/user-attachments/assets/286a34c0-075f-4b79-aafc-8015f26d8ab7" />


```sql
SELECT *
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="1262" height="464" alt="image" src="https://github.com/user-attachments/assets/c17c5a50-ceb0-42fc-afeb-944fb34d6311" />


**Question 8**
---
<img width="919" height="496" alt="image" src="https://github.com/user-attachments/assets/c85cd810-4e2f-4372-9439-d80031b0d97b" />


```sql
SELECT *
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (
        SELECT MAX(id)
        FROM customer
    )
);

```

**Output:**

<img width="1301" height="500" alt="image" src="https://github.com/user-attachments/assets/af17531a-b1dd-41f7-9ca6-89b85ada0ace" />


**Question 9**
---
<img width="886" height="689" alt="image" src="https://github.com/user-attachments/assets/32a2dec8-66d0-4258-aaef-dbb114b7687f" />


```sql
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;

```

**Output:**

<img width="1138" height="592" alt="image" src="https://github.com/user-attachments/assets/9b8c3a35-3d7d-490b-8bd8-390340108009" />


**Question 10**
---
<img width="878" height="469" alt="image" src="https://github.com/user-attachments/assets/4476576f-ccf1-4577-ab6a-97c4b70af66e" />


```sql
SELECT medication_id, medication_name, dosage
FROM Medications
WHERE dosage = (
    SELECT MIN(dosage)
    FROM Medications
);

```

**Output:**

<img width="792" height="439" alt="image" src="https://github.com/user-attachments/assets/b6b6dbca-4f5d-4c3a-be97-96c7b21b051b" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
