# enis
<?php
	$_db_host = "localhost";
	$_db_datenbank = "d024f4ae";
	$_db_username = "d024f4ae";
	$_db_password = "Andre1337!";

session_start();


$connection = mysql_connect($_db_host, $_db_username, $_db_password);

	$error = false;

if(isset($_POST['submit'])){

	$error = false;
	$username = $_POST['username'];
	$password = $_POST['password'];
	$password2 = $_POST['password2'];
	$email = $_POST['email'];

	if (empty($username)) {
		$error = true;
		echo '1';
	} else if (strlen($username) < 3) {
		$error = true;
		echo '2';
	} 
	
	if(!filter_var($email, FILTER_VALIDATE_EMAIL)) {
		echo '3';
		$error = true;
	} 

	if(strlen($password) == 0) {

		$error = true;
		echo '4';
	} else if(strlen($password) < 6) {
		$error = true;
		echo '5';
	}

	if($password != $password2) {
		echo '6';
		$error = true;
	}
	

	if(!$error){
	$query = "INSERT INTO users(username, password, password2, email) VALUES('$username', '$password', '$password2', '$email')";
	$res = mysql_query($query);


	if($res) {
		echo '7';
		unset($username);
		unset($password);
		unset($password2);
		unset($email);
	} else {
		echo '8';
		
	}


 }
}
?>
