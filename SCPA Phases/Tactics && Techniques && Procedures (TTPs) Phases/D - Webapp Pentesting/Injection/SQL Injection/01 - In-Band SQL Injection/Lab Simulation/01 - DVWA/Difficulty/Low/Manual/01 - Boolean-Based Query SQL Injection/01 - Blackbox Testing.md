# 01 - Blackbox Testing

Search Tag(s): #sql-injection #boolean-based #dvwa

Refer to [[Lab Simulation Setup/Webapps/DVWA/Setup#^214bb7|DVWA Lab Setup]] for the attacker machine to map the IP address in the `/etc/hosts`.

We have to understand from the developer's perspective. The webserver has PHP code as a server side. Let's take this PHP one line code as example. When the user authenticate to the form with his credentials which also can be exploited with unsantized user input.

```php
<?php
// Establish a database connection
$connect = mysqli_connect("localhost", "username", "password", "accountsdb");

// Check if connection was successful
if (!$connect) {
    die("Connection failed: " . mysqli_connect_error());
}

$username = $_POST['username'];
$password = $_POST['password'];

// Create SQL query to fetch data from 'users' table with unsanitized input
$sql = "SELECT * FROM users WHERE username = '$username' AND password = '$password'";

// Execute the query using mysqli_query function
$query = mysqli_query($connect, $sql);

// Check if the query was executed successfully
if ($query) {
    $result = mysqli_fetch_assoc($query);
    echo "Welcome, " . $result['username'] . "!";
} else {
    echo "Error: " . mysqli_error($connect);
}

// Close the database connection using mysqli_close function
mysqli_close($connect);
?>
```

The boolean conditions that helps us to look for differences in the web application's response.

```sql
' OR 1=1 --
' OR 1=2 --
```

The database server will not interpret it as PHP code. It will only recognize SQL queries and evaluate it. Observe when you include the boundaries by adding the single quote (`'`) as suffix and escaping it with comments (`--`) as prefix. Then in the middle of the SQL query containing a logical operator (`OR`) and always evaluate the response as true (`1=1`).

```sql
SELECT * FROM users WHERE username = '' OR 1=1 --' AND password = 'password123'
```

You can see the references below for better visualization. If you're a beginner then I recommend you to visit the link below.

---
## References

- [Hacksplaining: SQL Injection](https://www.hacksplaining.com/exercises/sql-injection)