# REVIRTIENDO CAMBIOS

Para continuar con el tutorial vamos a crear un par de archivos más en nuestro repositorio actual. 

```
$ touch script2.py README
$ git status
# On branch master 
# Untracked files: 
#   (use "git add <file>..." to include in what will be committed) 
# 
#	README 
#	script2.py 
nothing added to commit but untracked files present (use "git add" to track)
```

Efectivamente git sabe que hemos hecho cambios en nuestro repositorio y espera a que agreguemos los nuevos archivos y que confirmemos su seguimiento, procedamos entonces:

```
$ git add .
# On branch master 
# Changes to be committed: 
#   (use "git reset HEAD <file>..." to unstage) 
# 
#	new file:   README 
#	new file:   script2.py 
```

git nos solicita que confirmemos cambios, también nos da la opción de revertir la acción anterior con reset HEAD, veamos que sucede entonces:

```
$ git reset HEAD
# On branch master 
# Untracked files: 
#   (use "git add <file>..." to include in what will be committed) 
# 
#	README 
#	script2.py 
nothing added to commit but untracked files present (use "git add" to track)
```

Hemos revertido la acción anterior y volvemos a tener dos archivos nuevos sin agregar en nuestro repositorio, los agregaremos de nuevo para continuar con el tutorial.

```
$ git add .
$ git commit -am “segundo script y README”
[master fc59723] segundo script y README 
 0 files changed 
 create mode 100644 README 
 create mode 100644 script2.py 
```
```
$ git status 
# On branch master 
nothing to commit (working directory clean) 
```
```
$ git log --pretty=short 
commit fc597238a5147ea8ece42ca6817f932a366b6069 
Author: Mr. Floyd <mr.floyd@ues.edu.sv>

    segundo script y README 

commit 79ba623acf7741e21cc1b6ccb3435301405ec0d3 
Author: Mr. Floyd <mr.floyd@ues.edu.sv> 

    Hola mundo estilo CSHL 

commit 3ccd2e06ed65ce95f7af3df9ca28c0dfb5af5fed 
Author: Mr. Floyd <mr.floyd@ues.edu.sv> 

    script inicial 
```

El comando __log__ tiene varias opciones útiles (más información en la documentación oficial) que nos dan detalle de lo que hemos estado haciendo en nuestro repositorio, el comando anterior muestra el detalle de manera bastante amigable y sencilla al usuario.

Vamos a editar un archivo más para mostrar otras opciones útiles de git:

```
$ cat README
Comunidad de software y hardware libre UES FMOcc 
Introducción a git

$ git diff
diff --git a/README b/README 
index e69de29..d603bef 100644 
--- a/README 
+++ b/README 
@@ -0,0 +1,3 @@ 
+Comunidad de software y hardware libre UES FMOcc 
+ 
+Introducción a git
```

El comando __git diff__ compara lo que hay actualmente en nuestro directorio con lo que se tenia previamente confirmado, indica los cambios hechos que aun no han sido confirmados.

```
$ git commit -am "README"
```

Acabamos de confirmar los cambios en README.
¿Que sucede si nos equivocamos en algo al editar el archivo o si la descripción del commit no nos gusta del todo y queremos revertir la confirmación? Pues sencillo hagamos un reset al ultimo commit que hemos hecho:

```
$ git log -1 --pretty=short 
commit 592577537bf0587cc4bf80b57b74357081787690 
Author: Mr. Floyd <mr.floyd@ues.edu.sv>

    README 
```

Veamos cual fue el último commit hecho, ahora pasemos a revertir el commit

```
$ git reset --soft HEAD^
$ git status
# On branch master 
# Changes to be committed: 
#   (use "git reset HEAD <file>..." to unstage) 
# 
#	modified:   README 
```
```
$ cat README
Comunidad de software y hardware libre UES FMOcc 
Introducción a git
```

Hemos utilizado git reset --soft HEAD^ que revierte el ultimo commit realizado manteniendo los cambios que se hicieron en el archivo o archivos modificados, al usar git status vemos que efectivamente regresamos al estado anterior del commit, ahora podemos, si lo queremos, editar de nuevo el archivo y hacer un nuevo commit. 

Vamos a hacer commit de nuevo para continuar:

```
$ git commit -am "README actualizado"
[master e12b294] README actualizado 
 1 file changed, 3 insertions(+)
 ```
 
Si por casualidad queremos eliminar permanentemente un commit o varios, podemos usar el comando reset con la opción --hard y el ID del commit:
sintaxis: ```$ git reset --hard «commit sha1»```
Es importante mencionar que este comando es peligroso, ya que con esto estaríamos borrando los commit que se han hecho posteriormente al commit que hemos especificado, no habrá forma de revertir los cambios ¿o quizás si? 

__«tendríamos que investigar un poco, de paso aprendemos algo nuevo y lo compartimos acá...»__
 
 
Si por ejemplo queremos eliminar todos los archivos que no estan siendo seguidos por git en el repositorio actual git nos da un comando sencillo y util para esta tarea:

```
$ git clean -f
```

Lo anterior indica a git que borre todo lo que no ha sido previamente añadido al control de versión, para más informacion sobre este comando ir a la documentación ofical.
