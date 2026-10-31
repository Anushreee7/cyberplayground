# cyberplayground

## Contents
1. V1: Vulberable Web Application
2. SQL Injection Prevention
3. Reflected XSS Prevention
4. Web Application Update: comment.php
5. Stored XSS Prevention


## Attack 1: SQL injection prevention

prevention of SQL Injection through php is through the use of prepared statements which is also recommended by the OWASP : 

```
    $query = "SELECT * FROM users WHERE username= ? AND password= ? ";
    
    $stmt = mysqli_stmt_init($conn);
    if (!mysqli_stmt_prepare($stmt, $query)) {
	    echo "SQL error: " . mysqli_error($conn);
    } else {
	   mysqli_stmt_bind_param($stmt, "ss" , $username, $password);
	   mysqli_stmt_execute($stmt);
```



## Attack 2: Reflected XSS

XSS attacks can be prevented by the use of htmlspecialchars() alone, but ENT-QUOTES excludes the single quotation signs as well; Since the hackers can be using different languages to confuse the code configuration into passing their attack, UTF-8 tells PHP to use the modern, standard dictionary so hackers can't use weird symbols to bypass the security.

Injection: 
```
<script>alert("hack")</script>
<script>prompt("Session Expired enter password: ")<.script>
```



How it got secured:

```
    	    echo "<h2>Invalid Credentials: " . htmlspecialchars($username, ENT_QUOTES, 'UTF-8') . "</h2>";
```


### Sources Used:

YouTube: [
40: What are Prepared Statements and how to use them | PHP tutorial | Learn PHP programming ](https://www.youtube.com/watch?v=I4JYwRIjX6c)

W3 Schools: [PHP tutorials](https://www.w3schools.com/php/func_mysqli_query.asp)

## Attack 3: Stored XSS

In the same way as the reflected XSS, stored xss can be prevented using htmlspecialchars() with the extra ENT_QUOTES AND UTF-8 as well.

Injection:

```
<script>alert("hacked")</script>
```


```
  echo "<div>". htmlspecialchars($row['comment_text'], ENT_QUOTES, 'UTF-8') . "</div><br>";
```
