# GIT BÁSICO

Ya hemos configurado nuestro entorno git, ahora es hora de comenzar a trabajar con el.

Vamos a comenzar creando un directorio en el lugar que queramos y le diremos a git que tome el control de todo lo que en el hagamos:

```
$ mkdir practica-git && cd practica-git
$ git init
Initialized empty Git repository in ~/practica-git/.git/ 
```

git init creará un subdirectorio llamado __.git__ donde se encuentran los archivos necesarios para llevar el control de tu directorio actual.

```
$ ls -a
$ ls .git/
branches  config  description  HEAD  hooks  info  objects  refs
```

Comencemos con un comando que usaremos mucho a lo largo de este tutorial:

```
$ git status
# On branch master 
# 
# Initial commit 
# 
nothing to commit (create/copy files and use "git add" to track)
```

__git status__ nos da información sobre nuestro repositorio actual, nos dice si algo cambio, si hay conflicto, etc.

Creemos un archivo sencillo dentro de nuestro directorio actual y veamos que nos dice git status:

```
$ touch script.py 
$ git status
# On branch master 
# 
# Initial commit 
# 
# Untracked files: 
#   (use "git add <file>..." to include in what will be committed) 
# 
#	script.py 
nothing added to commit but untracked files present (use "git add" to track)
```

Nos damos cuenta que git ha detectado que hemos hecho cambios en nuestro directorio, en este caso hemos agregado un archivo nuevo y git nos pide que usemos __“git add”__ para poder llevar control de este archivo, procedamos entonces:

```
$ git add script.py
$ git status
# On branch master 
# 
# Initial commit 
# 
# Changes to be committed: 
#   (use "git rm --cached <file>..." to unstage) 
# 
#	new file:   script.py 
```

Hemos incluido nuestro archivo, pero falta un paso y es confirmar (commit) los cambios:

```
$ git commit -m “script inicial”
[master (root-commit) 3ccd2e0] script inicial 
 0 files changed 
 create mode 100644 script.py
$ git status
# On branch master 
nothing to commit (working directory clean)
```

git status nos dice que tenemos un directorio de trabajo limpio, esto quiere decir ya tenemos un repositorio git con un archivo en seguimiento y una confirmación inicial. Git además nos dice en que rama estamos trabajando, en nuestro caso “master” que es la creada por default (más adelante crearemos y usaremos ramas).

Como hemos visto el proceso de agregar un archivo para que git lleve su control consta de dos pasos, agregar (add) y confirmar (commit). El comando __git add «archivo»__ puede resultar tedioso si tenemos varios archivos y queremos agregarlos todos, pues tendríamos que agregar archivo por archivo, pero git nos ofrece otro comando útil: __git add .__ (el punto después del add indica a git que vamos a agregar al repositorio todos los archivos dentro de nuestro directorio, luego bastaría con hacer un commit para confirmar los cambios).

Git nos permite ver los commits que se han hecho en nuestro repositorio, para ello usaremos el comando __log__ así:

```
$ git log
commit 3ccd2e06ed65ce95f7af3df9ca28c0dfb5af5fed 
Author: Mr. Floyd <mr.floyd@ues.edu.sv> 
Date:   Fri Jul 18 23:39:18 2014 -0600 
 
    script inicial
```

Podemos notar que el commit tiene una serie de números y letras, eso es el identificador único (ID) que git asigno a nuestro commit, git utiliza el hash sha1 para identificar cada commit como único dentro de nuestro repositorio, por lo que podemos hacer algo como:

```
$ git show 3ccd2e06ed65ce95f7af3df9ca28c0dfb5af5fed
commit 3ccd2e06ed65ce95f7af3df9ca28c0dfb5af5fed 
Author: Mr. Floyd <mr.floyd@cshluesocc.org> 
Date:   Fri Jul 18 23:39:18 2014 -0600 

    script inicial 

diff --git a/script.py b/script.py 
new file mode 100644 
index 0000000..e69de29
```

con esto, decimos a git que nos muestre con detalle el commit con ID 3ccd2e06ed65ce95f7af3df9ca28c0dfb5af5fed. Escribir todo el ID del commit resulta un poco tedioso, pero no es necesario escribir todos los caracteres, podemos obtener el mismo resultado anterior haciendo:

```
$ git show 3ccd2e
```

__git show__ nos permite utilizar los primeros 5, 6 o 7 caracteres del ID del commit en lugar de los 40, con esto evitamos escribir tanto. También podemos usar el comando __show__ sin especificar  un id y git nos dará detalle del commit más reciente.

```
$ git show
```

Ahora vamos a modificar el script que hemos creado y ver como reacciona git ante los cambios que hagamos, para el ejemplo agregaremos un par de lineas:

Nota: con __cat__ mostramos las lineas que hemos agregado a nuestro  script.py, puedes  agregar las lineas que desees, al fin y al cabo solo nos interesa lo que nos muestre git.

```
$ cat script
#! /usr/bin/env python 

print "hola mundo, somos la CSHL"
$ git status
# On branch master 
# Changes not staged for commit: 
#   (use "git add <file>..." to update what will be committed) 
#   (use "git checkout -- <file>..." to discard changes in working directory) 
# 
#	modified:   script.py 
# 
no changes added to commit (use "git add" and/or "git commit -a")
```

Git nos informa que el archivo que creamos ha sido modificado y pide que confirmemos sus modificaciones, nos sugiere dos comandos, __“git add”__ o __“git commit -a”__, el primero ya lo hemos utilizado y sabemos que consta de dos pasos, agregar (add) y confirmar (commit), el segundo comando que nos sugiere puede efectuar los dos pasos anteriores de una sola vez, por conveniencia usaremos el segundo pero agregaremos una opción más, así:

```
$ git commit -am “Hola mundo desde la CSHL”
[master 79ba623] Hola mundo desde la CSHL 
 1 file changed, 3 insertions(+) 
 mode change 100644 => 100755 script.py 
```

Veamos ahora que información podemos obtener sobre los últimos cambios hechos:

```
$ git status
# On branch master 
nothing to commit (working directory clean)
```
```
$ git log –graph
* commit 79ba623acf7741e21cc1b6ccb3435301405ec0d3 
| Author: Mr. Floyd <mr.floyd@cshluesocc.org> 
| Date:   Sat Jul 19 00:36:48 2014 -0600 
| 
|     Hola mundo desde la CSHL 
|  
* commit 3ccd2e06ed65ce95f7af3df9ca28c0dfb5af5fed 
  Author: Mr. Floyd <mr.floyd@cshluesocc.org> 
  Date:   Fri Jul 18 23:39:18 2014 -0600 
  
      script inicial
```

Vemos como status nos muestra que no hay más cambios en nuestro archivos, el comando __log --graph__ nos muestra una pequeña  gráfica en a modo consola de los commits que hemos hecho.















