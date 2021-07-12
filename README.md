
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
