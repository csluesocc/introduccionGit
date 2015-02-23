##Ignorando archivos

Podemos también decirle a git que ignore ciertos archivos y estos no serán rastreados por git y no serán parte del repositorio aunque estos estén en nuestro directorio actual, esto es necesario muchas veces porque aveces los editores que usamos para trabajar crean archivos temporales en el directorio actual, archivos como ~script.py que realmente no queremos que sean parte de nuestro proyecto, para eso git tiene un archivo especial llamado __.gitignore__ que debemos crearlo y hacerle un commit en nuestra repo.

El archivo __.gitignore__ es un simple  archivo  de texto que indica que tipo archivos queremos que git ignore, creemos nuestro .gitignore:

```
$ touch .gitignore 
$ git status
# On branch master 
# Untracked files: 
#   (use "git add <file>..." to include in what will be committed) 
# 
#	.gitignore 
nothing added to commit but untracked files present (use "git add" to track
```

git  nos dice que hay un nuevo archivo, en el vamos a agregar lo siguiente: 

```
$ cat .gitignore 
# ignorar los archivos que coincidan con los siguientes patrones 

~* 
*.so 
*.log 
```

Agreguemos el archivo anterior a nuestro repositorio

```
$ git add .gitignore
$ git commit -am "ignorar archivos" 
[master 8597e52] ignorar archivos 
 1 file changed, 6 insertions(+) 
 create mode 100644 .gitignore 
$ git status
# On branch master 
nothing to commit (working directory clean)
```

Ahora podemos probar agregando un archivo que cumpla con los patrones que se especificaron en .gitignore, probemos si funciona:

```
$ touch ~temp 
$ git status 
# On branch master 
nothing to commit (working directory clean)
```

efectivamente git ha ignorado ese archivo, puedes agregar los patrones que consideres necesarios para que git ignore los archivos que coincidan con lo que has definido.

En .gitignore podemos usar expresiones regulares, por ejemplo, hemos usado __~*__ que indica a git que ignore todos los archivos que comienzen con el simbolo __~__, así podemos crear patrones para hacer que git se comporte de manera más inteligente. Notar que también hemos usado la almohadilla __#__ para escribir un comentario, en .gitignore todo el texto precedido por la alomadilla sera ignorado y no afectara el su funcionamiento.

Podemos ignorar directorios completos, por ejemplo:

```
#ignorar los directorios siguientes
bower/
libs/
```

Lo anterior le dice a git que ignore el contenido de los directorios bower y libs, podemos además decirle a git que ingnore todo el directorio excepto un ciertos archivos, por ejemplo:

```
#ignorar los directorios siguientes
bower/
libs/
#no ignorar el siguiente archivo
!libs/miScript.py
```

Le hemos dicho a git que ignore todos los archivos en el directorio libs/ excepto por el archivo miScript.py, simplemente hemos usado el simbolo __!__ para idicar que ese archivo no debe ser ignorado, esto es realmente util en proyectos grandes donde hay archivos que no deben ser ignorados.

Una lista extensa de ejemplos de .gitignore para diferentes tipos de proyectos puede ser encontrada en: https://github.com/github/gitignore. Más información de gitignore: http://git-scm.com/docs/gitignore.




