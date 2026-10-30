# cyberplayground
This contains the code used for the making of the web application; as the versions develop, they tackle a specific cyber attack

## Contents
1. V1: Vulberable Web Application
2. SQL Injection Prevention
3. Reflected XSS Prevention
4. Web Application Update: comment.php
5. Stored XSS Prevention

### V1: Vulnerable Web Application


## Attack 1: SQL injection prevention

### Sources Used:

YouTube: [
40: What are Prepared Statements and how to use them | PHP tutorial | Learn PHP programming ](https://www.youtube.com/watch?v=I4JYwRIjX6c)

W3 Schools: [PHP tutorials](https://www.w3schools.com/php/func_mysqli_query.asp)



prevention of SQL Injection through php is through the use of prepared statements which is also recommended by the OWASP : 

`
$query = "SELECT * FROM users WHERE username= ? AND password= ? ";
    
    $stmt = mysqli_stmt_init($conn);
    
    if (!mysqli_stmt_prepare($stmt, $query)) {
	  
      echo "SQL error: " . mysqli_error($conn);
    
    } else {
	  
     mysqli_stmt_bind_param($stmt, "ss" , $username, $password);
	   
     mysqli_stmt_execute($stmt);
`
