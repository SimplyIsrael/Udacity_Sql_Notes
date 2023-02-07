## Lesson 2: SQL joins

### Outlines
* Creating Joins
* Using Primary-Foreign keys
* Integrating Aliases
* Join types
* Integrating filter with joins

### Why are different sorts of data stored in different tables?
1.	Some sorts of data are updated more frequently than other sorts and it’s more efficient and safer to store them separately
2.	Storing data in separate tables allows you to access the data much more quickly, because each table contains only a portion of the total available data

### Three questions about normalization:
1.	Are the tables storing logical groupings of data?
2.	Can I make changes in a single location, rather than in many tables for the same information?
3.	Can I access and manipulate data quickly and efficiently?

### Inner Joins
Joins allow us to pull data from more than one table at a time.
```sql
SELECT orders.*,
       accounts.*
FROM orders 
JOIN accounts
ON orders.account_id = accounts.id;
```
Here, we SELECT every column from both the orders table and the accounts table. We need to use the dot notation to specify from which table we’re getting a particular column. In this case, we’re using a wildcard to get all columns. (We could have skipped listing both tables and just used the wildcard, in this case) We’ll get those columns FROM the orders table, JOINed with the accounts table. We’ll join these two tables ON two particular columns: the account_id column from orders and the id column from accounts. 

You can join more than two tables like this:
```sql
SELECT *
FROM web_events
JOIN accounts
ON web_events.account_id = accounts.id
JOIN orders
ON accounts.id = orders.account_id
```
Here, we SELECT all columns from all tables, starting FROM the web_events table and JOINing the accounts table ON web_events.account_id and accounts.id. Then we JOIN the orders table ON accounts.id and orders.account_id. Note that we connect web_events to accounts and then connect accounts to orders.
