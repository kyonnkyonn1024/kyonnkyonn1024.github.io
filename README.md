```
<?php

$id = time();
$kind = $_SESSION['kind'];
$star = $_SESSION['star'];
$message = htmlspecialchars($_SESSION['message'], ENT_QUOTES, 'UTF-8');
$userid = $_SESSION['EMAIL'];

//mysql接続
$dsn = 'mysql:dbname=データベース名;host=localhost';
$user = 'root';
$password = 'パスワード';
try{
    $dbh = new PDO($dsn, $user, $password);
}catch (PDOException $e){
    print('Error:'.$e->getMessage());
    die();
}


// データの追加
$sql = 'INSERT INTO formdata(id, kind, star, message, userid) VALUES("'.$id.'","'.$kind.'","'.$star.'","'.$message.'","'.$userid.'")';
$stmt = $dbh -> prepare($sql);
$stmt -> execute();
?>
```
