[ createuser.php ]
<?php

if ($_SERVER["REQUEST_METHOD"] == "POST"){   
   $db = new mysqli('localhost', 'root', 'cisco', 'test');     
   if($db->connect_error){    
      die('Not Connected : ' . $db->connect_error);  
   }
     
   
$sql2 = "select ID from user where ID='$_POST[ID]'";   
   $result2 = $db->query($sql2);   
   if($result2->num_rows !== 0){   
      die("User Exists!");  
   }   
   $sql = "insert into user (ID,PW) values ('$_POST[ID]','$_POST[PW]')";   
   $result = $db->query($sql);  
   if($result){   
      echo '<p>' .  "List of users" . '</p>';
      echo "-------------------------------------------------------";
      
         $conn=mysqli_connect('localhost', 'root', 'cisco', 'test');
         $sql="select * from user";
         $result=mysqli_query($conn, $sql);

         while( $row = mysqli_fetch_array( $result ) ) {
          echo '<p>' ."ID : ". $row[ 'ID' ] . "&emsp;&emsp;" . "PW : ". $row[ 'PW' ] . '</p>';
      }
  
   }
   else{    
      echo "ERROR ";   
   }
}
?>

<html>
<h1> CREATE A NEW USER! </h1>
<form action="" method="post">   
   <label for="ID">NEW ID : </label>      
      <input type="text" name="ID">  
   <label for="PW">NEW PW : </label>    
      <input type="text" name="PW">  
   <input type="submit" value="submit">   
</form>
</html>
