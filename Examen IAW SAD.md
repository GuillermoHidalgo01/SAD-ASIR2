# EXAMEN IAW SAD

# Script que nos crea automaticamente la base de datos y el fichero wp.cli.phar para el funcionamiento del propio gestor de contenido

```powershell
$var = "examen_guillermo"

cd C:\xampp\htdocs\works

foreach($usuarios in $var)

{

    $usuarios

    New-Item -ItemType Directory -Name $usuarios -Force

    cd C:\xampp\htdocs\works\$usuarios

    php.exe C:\xampp\php\wp-cli.phar core download

    php.exe C:\xampp\php\wp-cli.phar config create --dbname=$usuarios --dbuser=root

    # Una vez creado el fichero wp-config.php con el comando wp config create --dbname=wptest --dbuser=miusuario --dbpass=miclave --locale=es_ES

    # Crea la base de datos con la estructura de WordPress

    php.exe C:\xampp\php\wp-cli.phar db create

    php.exe C:\xampp\php\wp-cli.phar core install --url=localhost/works/$usuarios --title="Este es el sitio de $usuarios" --admin_user=guillermo --admin_password=Andel_1928 --admin_email=mi@email.com

    cd ..
    }
```

# URL DE ACCESO

http://localhost/works/examen_guillermo/

Usuario:guillermo
Passwd: Andel_1928


# Creamos los ficheros .php para poder subir los archivos, esto de hace en la carpeta de htdocs y creamos la carpeta de uploads. Creamos fichero upload.php y formulario.php

# Fichero formulario.php
```powershell
<!DOCTYPE html>
<html>
<body>

<form action="upload.php" method="post" enctype="multipart/form-data">
  Select image to upload:
  <input type="file" name="fileToUpload" id="fileToUpload">
  <input type="submit" value="Upload Image" name="submit">
</form>

</body>
</html>
```

# Fichero upload.php

```powershell
<?php
$target_dir = "uploads/";
$target_file = $target_dir . basename($_FILES["fileToUpload"]["name"]);
$uploadOk = 1;
$imageFileType = strtolower(pathinfo($target_file,PATHINFO_EXTENSION));

// Check file size
if ($_FILES["fileToUpload"]["size"] > 500000) {
  echo "Sorry, your file is too large.";
  $uploadOk = 0;
}

// Check if $uploadOk is set to 0 by an error
if ($uploadOk == 0) {
  echo "Sorry, your file was not uploaded.";
// if everything is ok, try to upload file
} else {
  if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $target_file)) {
    echo "The file ". htmlspecialchars( basename( $_FILES["fileToUpload"]["name"])). " has been uploaded.";
  } else {
    echo "Sorry, there was an error uploading your file.";
  }
}
?>
```
# Nuestro virus ----->
```powershell
Start-Proccess cmd
```
# Ejecución de nuestro virus
```powershell
Start-BitsTransfer -Source 'https://localhost/uploads/virus.ps1'
.\virus.ps1
```
