---
name: SQL Injection
severity: high
cvss-score: 8.6
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:N/A:N
cwe-id: CWE-89
cwe-name: SQL Injection
compliance:
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.12, A.8.26
  owasp10: A3
  pci: 6.5.1

---            

SQL Injections are the most common form of injections because SQL databases are very popular in dynamic web applications. This vulnerability allows an attacker to tamper existing SQL queries performed by the web application. Depending on the queries, the attacker might be able to access, modify or even destroy data from the database.

Since databases are commonly used to store private data, such as authentication information, personal user data and site content, if an attacker gains access to it, the consequences are typically very severe, ranging from defacement of the web application to users data leakage or loss, or even full control of the web application or database server.

## How to fix

{% tabs sql-injection %}
{% tab sql-injection generic %}
To fix an SQL Injection you should use Prepared Statements. If an application exclusively uses prepared statements, the developer can be sure that no SQL injection will occur.
Prepared Statements can be thought of as a kind of compiled template for the SQL that an application wants to run, that can be customized using variable parameters.

As an added bonus, if you're executing the same query several times, then it'll be even faster than when you're not using prepared statements. This is because when using prepared statements, the query needs to be parsed (prepared) only once, but can be executed multiple times with the same or different parameters. 
{% endtab %}

{% tab sql-injection php %}
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

{% endtab %}

{% endtabs %}
