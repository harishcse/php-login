# php-login
php basic login page
<!DOCTYPE html>
<html>
<head><!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap-theme.min.css">

<!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js"></script>
	<title></title>
	<style type="text/css">
	body
	{
		//background-color:#008B8B	 ;
		//color:white;
	}


h3{text-align: center;
text-decoration: blink;}
	</style>

</head>
<body>
<?php 

if(isset($_POST['sub']))
{
	 $username = $_POST['username'];
     $mail = $_POST['mail'];
     $pasword =$_POST['password'];
     $num=$_POST['num'];
     
    
	
   $dbhost = 'localhost';
   $dbuser = 'root';
   $dbpass = '';
   $conn = mysql_connect($dbhost, $dbuser, $dbpass);
   if(! $conn )
   {
     die('Could not connect: ' . mysql_error());
   }
   echo 'Connected successfully';
   
   $db = mysql_select_db('hari');
   
   $query = mysql_query("INSERT INTO user(name,email,password,mobile)values('{$username}','{$mail}','{$pasword}','{$num}')");
   
   if(!$query)
   die(mysql_error());
  
   mysql_close($conn);
	
}

   
?>


<h3 >Sign Up</h3> 

<div class="container">

<form  action="first.php" method = "post" class="form-horizontal">
  <div class="form-group">
    <label for="input" class="col-sm-5 control-label">User Name :</label>
    <div class="col-sm-4">
      <input type="text" name = "username" class="form-control"  placeholder="User name">
    </div>
  </div>
  <div class="form-group">
    <label for="inputEmail3" class="col-sm-5 control-label">Email  :</label>
    <div class="col-sm-4">
      <input type="email" name="mail" class="form-control" id="inputEmail3" placeholder="Email">
    </div>
  </div>
  <div class="form-group">
    <label for="pass word" class="col-sm-5 control-label">Password :</label>
    <div class="col-sm-4">
      <input type="password"  name="password" class="form-control" id="pass word" placeholder="Password">
    </div>
  </div>
  <div class="form-group">
    <label for="mobile nuber" class="col-sm-5 control-label">Mobile Number :</label>
    <div class="col-sm-4">
      <input type="values" name="num" class="form-control"  placeholder="Mobile Number">
    </div>
  </div>
  <div class="form-group">
    <div class="col-sm-offset-5 col-sm-7">
      <div class="radio-inline">
        <label>
          <input type="radio"  name="male"> male &nbsp	 &nbsp&nbsp &nbsp 
           <input type="radio" name="female"> female
        </label>
      </div>
    </div>
    <div class="col-sm-offset-5 col-sm-7">
      <div class="radio-inline">
        <label>
         
        </label>
      </div>
    </div>
  </div>
  <div class="form-group">
    <div class="col-sm-offset-5 col-sm-10">
      <button type="submit" class="btn btn-default" name="sub">Sign in</button>

      <button type="submit" class="btn btn-default">Cancel</button>
    </div>
  </div>
</form>
</div>


</body>
</html>
