To fix an SQL Injection in PHP, you should use Prepared Statements. Prepared Statements can be thought of as a kind of compiled template for the SQL that an application wants to run, that can be customized using variable parameters.

PHP's PDO extension supports Prepared Statements, so that's probably your best option.

In the example below you can see the use of prepared statements. Variables ```$username``` and ```$hashedPassword``` come from user input.

```
$stmt = $dbg->prepare("SELECT id, name FROM users
                       WHERE username=? AND password=?");
$stmt->bindParam(1, $username);
$stmt->bindParam(2, $hashedPassword);
if ($stmt->execute()) {
	$user = $stmt->fetch();
	if ($user) {
		$_SESSION['authID'] = $user['id'];
		echo "Hello " . $user['name'];
	} else {
		echo "Invalid Login";
	}
}
```  

As an added bonus, if you're executing the same query several times, then it'll be even faster than when you're not using prepared statements. This is because when using prepared statements, the query needs to be parsed (prepared) only once, but can be executed multiple times with the same or different parameters. 
