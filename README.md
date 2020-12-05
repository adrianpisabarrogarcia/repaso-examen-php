# Repaso de examen PHP

### Sesiones

```php
session_start(); session_destroy(); //Comienza y Destruye sesión
session_unset(); //Elimina la sesión

//Encontrar un valor en la sesión
$mystring = 'abc';
$findme   = 'a';
$pos = strpos($mystring, $findme);
```

### Cookies

```php
setcookie("idioma", "castellano", time() + 7*24*60*60);
$usuario = $_COOKIE['usuario'];
setcookie("usuario", NULL, -1)
```

### Header Location

```php
header('Location: http://www.example.com/');
```

### BBDD

```sql
//Acceso y carga de script .sql
$ mysql -u root -p < biblio.sql

//Insert
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

//Update
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

//Delete
DELETE FROM table_name WHERE condition;

//Select
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

### array_push

```php
array_push($_SESSION["usuarios"],array(
        "codigo"=>$codigo,
        "nombre"=>$nombre,
        "apellidos"=>$apellidos,
    );
```

### array asociativo

```php
$equipo = array(portero=>'Cech', defensa=>'Terry', medio=>'Lampard', 
delantero=>'Torres');
 
foreach($equipo as $posicion=>$jugador)
	{
	echo "El " . $posicion . " es " . $jugador;
	echo "<br>";
	}
```

### Establecer conexión

```php
function connect(){
	try {
		# MySQL
		$dbh= new PDO("mysql:host=$host;dbname=$dbname", $user, $pass);   
	}catch(PDOException $e) {
		echo $e->getMessage();
  }
}

function mostrarEdad($dbh, $edad){
	// Incluir parámetros con la sintaxis :edad
$data = array('edad' => 15 );
	$stmt = $dbh->prepare("SELECT nombre, apellidos
	     FROM alumnos
			 WHERE edad > :edad");
  $stmt->setFetchMode(PDO::FETCH_OBJ);
	$stmt->execute($data);
}

function close(){
   /**
    * Una conexión a base de datos con PDO
    * permanecerá abierta mientras exista
    * el objeto PDO creado
    * */
		$dbh = null
;}

// Mostramos los resultados obtenidos
while($row = $stmt->fetch()) {
		echo $row->nombre . "\n";
		echo $row->apellidos . "\n";
		echo $row->edad . "\n";
}

//Saber si hay más de una línea o no
if ($stmt->rowcount() > 0) {
    return false;
}else{
		return true;
}
```
