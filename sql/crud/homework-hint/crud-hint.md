# Hint for MySQL CRUD Homework

## Homework 1

### Solution 1: Multiple tables select
```sql
CREATE TABLE new_agents AS
    SELECT DISTINCT
        agents.*
    FROM
        agents, customer
    WHERE
        agents.WORKING_AREA = 'London'
    AND
        agents.AGENT_CODE = customer.AGENT_CODE
    AND
        customer.CUST_COUNTRY = 'UK';

ALTER TABLE new_agents ADD PRIMARY KEY(AGENT_CODE);
```

### Solution 2: JOIN

```sql
CREATE TABLE `new_agents` AS SELECT DISTINCT
    `agents`.*
 FROM
     `agents`
     JOIN `customer` ON `agents`.`AGENT_CODE` = `customer`.`AGENT_CODE`
 WHERE
    `agents`.`WORKING_AREA` = "London"
    AND `customer`.`CUST_COUNTRY` = "UK";

ALTER TABLE `new_agents` ADD PRIMARY KEY ( `AGENT_CODE` );
```


They are the same, but with a different syntax. So you shouldn't expect any performance difference between the two syntaxes. However the the last syntax(ANS SQL-92 syntax) is the recommended,

## Homework 2

```sql
UPDATE `agents`
SET COMMISSION = COMMISSION -.02
WHERE
        `agents`.`AGENT_CODE` = (
        -- Subquery to select first agent code has smallest total payment 
        SELECT
            `customer`.`AGENT_CODE`
        FROM
            `customer`
        GROUP BY
            `customer`.`AGENT_CODE`
        ORDER BY
            SUM( `customer`.`PAYMENT_AMT` ) ASC
        LIMIT 1
    );
```


## Homework 3

```sql
SELECT
	* 
FROM
	`customer`
	JOIN `agents` ON `customer`.`AGENT_CODE` = `agents`.`AGENT_CODE` 
WHERE
	`customer`.`GRADE` = 3 
	AND NOT `customer`.`CUST_COUNTRY` = "India" 
	AND `customer`.`OPENING_AMT` < 7000 
	AND `agents`.`COMMISSION` < 0.12;
```