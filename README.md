<html>
<head>
<title> User Registration Page</title>
<script language="javascript">
function validate()
{
var nam = document.f1.uname.value;
if(nam=="")
{
alert("Please enter name");
document.f1.uname.focus;
return false;
}
var pwd = document.f1.pass.value;
if(pwd=="")
{
alert("Please enter Password");
document.f1.pass.focus;
return false;
}
var email = document.f1.email.value;
if(email=="")
{
alert("Please enter youe email");
document.f1.email.focus;
return false;
}
var phno = document.f1.phone.value;
len=phno.length
if(phno=="" || len != 10)
{
alert("Please enter phno or should be strictly 10 digits");
document.f1.phone.focus;
return false;
}
}
</script>
</head>
<body>
<br/><br/><br/>
 <center>
<form name="f1" action="insertData.php" method="post" onsubmit="javascript:return 
validate()">
<table border="3" cellpadding="0" cellspacing="0">
<tr>
<td>
<table cellspacing="10">
<tr>
 <td colspan="2" align="center"><h2><u>User Registration Form</u></h2></td>
 </tr>
<tr>
 <td> User Name</td>
 <td><input type="text" name="uname" size="50"></td>
</tr>
<tr>
 <td> Password</td>
 <td><input type="password" name="pass" size="50"></td>
</tr>
<tr>
 <td> E-mail</td>
 <td><input type="text" name="email" size="50"></td>
</tr>
<tr>
 <td> Phone</td>
 <td><input type="text" name="phone" size="15"></td>
</tr>
<tr>
 <td colspan="2" align="center"><input type="submit" value="submit"></td>
</tr>
</table>
</td>
</tr>
</table>
</form>
</center>
</body>
</html>
<?php 
$conn = mysql_connect("localhost","root","");
if($conn)
 echo "Connected to database!!!";
else
 echo "Failed to Connect:".mysql_error();
 mysql_select_db("test",$conn) or die("No Database existing:".mysql_error());
if(isset($_REQUEST['uname']))
{
$uname=$_REQUEST['uname'];
$pass=$_REQUEST['pass'];
$email=$_REQUEST['email'];
$phno=(float)$_REQUEST['phone'];
 $query = "INSERT INTO registration VALUES('$uname','$pass','$email','$phno')";
mysql_query($query);
$result = mysql_query("select * from registration");
?>
<html>
<body>
<br/><br/><br/>
<p align="right"><a href="registration.html">[Registration Page]</a></p>
<center>
<font face="verdana" size="4">
<table border="1" cellpadding="0" cellspacing="0">
<tr>
<th colspan="4" align="center">User List</td>
 </tr>
 <tr>
 <th> S.No.</th>
 <th> User Name</th>
 <th> Email</th>
 <th>Phone</th>
</tr>
<?php $num=1; while($row = mysql_fetch_array($result))
{ ?>
<tr>
 <td><?php echo $num++; ?> </td> 
 <td><?php echo $row['uname']; ?> </td>
 <td><?php echo $row['email']; ?> </td>
 <td><?php echo $row['phno']; ?> </td>
</tr>
<?php }?>
</table>
</center>
</body>
</html>
<?php } ?>
