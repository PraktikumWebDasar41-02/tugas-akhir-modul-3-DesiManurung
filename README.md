# tugas-akhir-modul-3-DesiManurung
tugas-akhir-modul-3-DesiManurung created by GitHub Classroom

<?php
session_start();
if(isset($_SESSION["username"]) && isset($_SESSION["password"])) {
}
?>
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
		<form action="konek.php" method="POST" enctype="multipart/form-data">
			<table>
				<tr>
			<h2><center> Desi J Manurung </h2></center><br><br>
				<tr>
					<img alt="Desi Manurung" src="Desi.jpg" height="100" width="200" />
					<img alt="Desi Manurung" src="Desi.jpg" height="100" width="200" />
					<img alt="Desi Manurung" src="Desi.jpg" height="100" width="200" />
					<img alt="Desi Manurung" src="Desi.jpg" height="100" width="200" /><br>

				</tr>
						<tr>
							<td>Upload Foto : </td>
        					
                            <input type="file" name="fileToUpload" id="fileToUpload">
                             <input type="submit" value="Upload Image" name="submit">
						</tr>
					</table>
					<a href="logout.php">Logout</a>
		</body>
</html>
</form>


=========================================================================================================================

<?php  
 $host = "localhost";  
 $user = "root";  
 $password = "";  
 $db = "buat_instagram";  
 $conn = mysqli_connect($host,$user,$password, $db); 
 ord("koneksi gagal") ;
 try{
 	$pdo = new PDO("mysql:host={$host}; dbname={$db};", $user,$password);
 	$pdo -> setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
 }	
 catch (PDOException $e){
 	print "koneksi atau query bermasalah : " . $e -> getMessage() . "<br>";
 	die();
 }
 	if (isset($POST['submit'])) {
 		$user = $_POST['namauser'];  
 		$pass = $_POST['password'];  
 		$foto = $_FILES['gambar']['name'];
 		$tmp_name = $_FILES['gambar']['tmp_name'];
 		$dir_foto = "foto/";
 		$target_foto = $dir_foto . $foto;

	 	$query = $pdo -> prepare("INSERT INTO instagram_sederhana VALUES ('$user' , '$pass',  '$foto')");
	 	$query -> execute();
	 
 	}
?>
=============================================================================================================================

<!DOCTYPE html>
<html>
<head>
	<title><h2>Login Disini</h2></title>
</head>
<body>
	<form action="formnya.php" method="POST">
	<table>
		<tr>
			<td>Username</td>
			<td>:</td>
			<td><input type="text" name="username"></td>
		</tr>
		<tr>
			<td>Password</td>
			<td>:</td>
			<td><input type="password" name="password"></td>
		</tr>
		<tr>
			<td></td>
			<td><input type="submit" name="login" value="Login" class="form1.php"> <input type="reset" value="Batal"></td>
		</tr>
	</table>
</form>

==============================================================================================================================

<?php 
session_start();
session_destroy();
header("Location: login.php");
?>

==============================================================================================================================
