
页面分析：
* 登录界面  login.html
* 登陆处理页面 dologin.php
* 登陆成功页面 welcome.php

登录页面 login.html

```
<!DOCTYPE html> 
<html> 
<head> 
<meta charset="UTF-8"> 
<title>登录</title> 
<style type="text/css"> 
form { 
  text-align: center; 
} 
</style> 
</head> 
<body> 
  <form action="dologin.php" method="post" > 
    用户名:<input type="text" name="username" id="username"><br> 
    密  码:<input type="password" name="password" id="password"><br> 
    <input type="submit" value="登录"> 

  </form> 
</body>
```
![](/images/php/01.png)


dologin.php



```
<!doctype html> 
<html> 
<head> 
  <meta charset="UTF-8"> 
  <title>登录系统的后台执行过程</title> 
</head> 
<body> 
  <?php 
    session_start();
    $username=$_REQUEST["username"]; 
    $password=$_REQUEST["password"];
  
    $con=mysql_connect("localhost","phpdemo","4wj7fGAKJR2ddXDx");
    if (!$con) { 
      die('数据库连接失败'.$mysql_error()); 
    } 
    mysql_select_db("phpdemo",$con);
    $dbusername=null; 
    $dbpassword=null; 
    $result=mysql_query("select * from users where username ='{$username}' ;");
    while ($row=mysql_fetch_array($result)) { 
      $dbusername=$row["username"]; 
      $dbpassword=$row["password"]; 
    } 
    if (is_null($dbusername)) {
  ?> 
  <script type="text/javascript"> 
    alert("用户名不存在"); 
    window.location.href="login.html"; 
  </script> 
  <?php 
    } 
    else { 
      if ($dbpassword!=$password){ 
  ?> 
  <script type="text/javascript"> 
    alert("密码错误"); 
    window.location.href="login.html"; 
  </script> 
  <?php 
      } 
      else { 
        $_SESSION["username"]=$username; 
  ?> 
  <script type="text/javascript"> 
    window.location.href="welcome.php"; 
  </script> 
  <?php 
      } 
    } 
  mysql_close($con);//关闭数据库连接，如不关闭，下次连接时会出错 
  ?> 
</body> 
</html>
```

welcome.php


```
<!doctype html> 
<html> 
<head> 
<meta charset="UTF-8"> 
<title>欢迎登录界面</title> 
</head> 
<body> 
  
<?php
session_start (); 
 ?> 
欢迎登录<?php
  echo "${_SESSION["username"]}";//显示登录用户名 
  ?><br> 
您的ip：<?php
  echo "${_SERVER['REMOTE_ADDR']}";//显示ip 
  ?> 
<br> 
浏览器版本： 
<?php
  echo "${_SERVER['HTTP_USER_AGENT']}";//浏览器版本信息 
  ?> 
 

</body> 
</html>
```



![](/images/php/02.png)




