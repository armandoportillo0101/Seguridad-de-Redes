## Descripción 
```
I sent out 2 invitations to all of my friends for my birthday! I'll know if they get stolen because the two invites look similar, and they even have the same md5 hash, but they are slightly different! You wouldn't believe how long it took me to find a collision. Anyway, see if you're invited by submitting 2 PDFs to my website. [http://mercury.picoctf.net:55343/](http://mercury.picoctf.net:55343/)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
Al mirar la página web, se nos dice que carguemos dos archivos, no cualquier archivo, sino 2 PDF al sitio web. Sugerencia: las dos invitaciones se ven similares e incluso tienen el mismo hash md5, ¡pero son ligeramente diferentes!

Inmediatamente, habla sobre colisiones MD5. Fui a Google y lo comprobé. Me encontré con un sitio fantástico, cuyo enlace se encuentra en Notas Adicionales. Puedes descargar según tus preferencias, si estás usando Windows o Linux. Después de descargar, cambia o renombra el archivo a file.pdf (agrega el .pdf), porque ese es el formato para cargar, y despues de cargar ambos archivos obtuve:
<?php  
  
if (isset($_POST["submit"])) {    $type1 = $_FILES["file1"]["type"];    $type2 = $_FILES["file2"]["type"];    $size1 = $_FILES["file1"]["size"];    $size2 = $_FILES["file2"]["size"];    $SIZE_LIMIT = 18 * 1024;  
  
    if (($size1 < $SIZE_LIMIT) && ($size2 < $SIZE_LIMIT)) {  
        if (($type1 == "application/pdf") && ($type2 == "application/pdf")) {            $contents1 = file_get_contents($_FILES["file1"]["tmp_name"]);            $contents2 = file_get_contents($_FILES["file2"]["tmp_name"]);  
  
            if ($contents1 != $contents2) {  
                if (md5_file($_FILES["file1"]["tmp_name"]) == md5_file($_FILES["file2"]["tmp_name"])) {                    highlight_file("index.php");  
                    die();  
                } else {  
                    echo "MD5 hashes do not match!";  
                    die();  
                }  
            } else {  
                echo "Files are not different!";  
                die();  
            }  
        } else {  
            echo "Not a PDF!";  
            die();  
        }  
    } else {  
        echo "File too large!";  
        die();  
    }  
}  
  
// FLAG: picoCTF{c0ngr4ts_u_r_1nv1t3d_aad886b9}  
  
?>  
<!DOCTYPE html>  
<html lang="en">  
  
<head>  
    <title>It is my Birthday</title>  
  
  
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css" rel="stylesheet">  
  
    <link href="https://getbootstrap.com/docs/3.3/examples/jumbotron-narrow/jumbotron-narrow.css" rel="stylesheet">  
  
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>  
  
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>  
  
  
</head>  
  
<body>  
  
    <div class="container">  
        <div class="header">  
            <h3 class="text-muted">It is my Birthday</h3>  
        </div>  
        <div class="jumbotron">  
            <p class="lead"></p>  
            <div class="row">  
                <div class="col-xs-12 col-sm-12 col-md-12">  
                    <h3>See if you are invited to my party!</h3>  
                </div>  
            </div>  
            <br/>  
            <div class="upload-form">  
                <form role="form" action="/index.php" method="post" enctype="multipart/form-data">  
                <div class="row">  
                    <div class="form-group">  
                        <input type="file" name="file1" id="file1" class="form-control input-lg">  
                        <input type="file" name="file2" id="file2" class="form-control input-lg">  
                    </div>  
                </div>  
                <div class="row">  
                    <div class="col-xs-12 col-sm-12 col-md-12">  
                        <input type="submit" class="btn btn-lg btn-success btn-block" name="submit" value="Upload">  
                    </div>  
                </div>  
                </form>  
            </div>  
        </div>  
    </div>  
    <footer class="footer">  
        <p>&copy; PicoCTF</p>  
    </footer>  
  
</div>  
  
<script>  
$(document).ready(function(){  
    $(".close").click(function(){  
        $("myAlert").alert("close");  
    });  
});  
</script>  
</body>  
  
</html>
Y solo es cuestion de buscar la bandera en el codigo.

picoCTF{c0ngr4ts_u_r_1nv1t3d_aad886b9}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
[https://www.mscs.dal.ca/~selinger/md5collision/](https://www.mscs.dal.ca/~selinger/md5collision/)
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias