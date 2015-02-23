## REMOVER Y MOVER ARCHIVOS

Si queremos eliminar archivos de nuestro repositorio, git ofrece otro comando útil llamado __git rm__ muy similar al comando rm unix.

Hablemos un poco sobre lo que hace este comando __git rm__, este elimina el o los archivos de nuestro repositorio y pide una confirmación para mantener el registro, el problema con este comando es que elimina el archivo del repositorio y del directorio en el que estamos trabajando, es como hacer __rm «archivo»__ en una terminal GNU/Linux (pero si formo parte del histórico de git, es posible recuperarlo), git es bondadoso y ofrece la opción de eliminar el archivo del repositorio pero dejando el archivo intacto en nuestro directorio. 
Si hemos hecho commit a un archivo por accidente, podemos usar __git rm --cahed «archivo»__ git lo dejara tal y como estaba antes de hacer el commit, veamos esto con un ejemplo sencillo:

Vamos a crear un archivo y lo incluiremos “accidentalmente” a nuestro repositorio.

```
$ echo “Oops!” > oops
$ git rm oops
fatal: pathspec 'oops' did not match any files
```

La operación no funciona porque el archivo aun no es parte de nuestro repositorio.

```
$ git add oops
$ git commit -am “commit accidental”
[master 8127794] commit accidental 
 1 file changed, 1 insertion(+) 
 create mode 100644 oops

$ git log -1 --pretty=short
commit 812779449b6fb39450d1426899a39945b340fb19 
Author: Mr. Floyd <mr.floyd@cshluesocc.org>

    commit accidental
```

Hemos agregado el archivo “accidentalmente” a nuestro repositorio. Como no lo queríamos agregar, pero si queremos mantenerlo en nuestro directorio procedamos a quitarlo del repositorio:

```
$ git rm --cached oops 
rm 'oops' 
```
```
$ git status 
# On branch master 
# Changes to be committed: 
#   (use "git reset HEAD <file>..." to unstage) 
# 
#	deleted:    oops 
# Untracked files: 
#   (use "git add <file>..." to include in what will be committed) 
# 
#	oops 

$ ls
oops  README  script2.py  script.py
```
```
$ git commit -am “oops elimiado del repositorio”
[master 22592c0] oops elimiado del repositorio 
 1 file changed, 1 deletion(-) 
 delete mode 100644 oops

$ git status 
# On branch master 
# Untracked files: 
#   (use "git add <file>..." to include in what will be committed) 
# 
#	oops 
```

Git ha hecho bien su trabajo, ha borrado del repositorio el archivo pero lo mantiene intacto en nuestro directorio. Agregaremos de nuevo el archivo y esta vez lo borraremos con git rm.

```
$ git add oops 
$ git commit -am "commit accidental" 
[master 43af71f] commit accidental 
 1 file changed, 1 insertion(+) 
 create mode 100644 oops 
$ git rm oops
rm 'oops

$ ls
README  script2.py  script.py 

$ git status 
# On branch master 
# Changes to be committed: 
#   (use "git reset HEAD <file>..." to unstage) 
# 
#	deleted:    oops 
# 
```
```
$ git commit -am “oops borrado correctamente”
[master 0f6d43a] oops borrado correctamente 
 1 file changed, 1 deletion(-) 
 delete mode 100644 oops 
```

Detengámonos un poco y veamos los últimos 5 commits que hemos hecho:

```
$ git log -5 --pretty=short 
commit 0f6d43a9c0687fa70ca95700aae45d75b782bb43 
Author: Mr. Floyd <mr.floyd@cshluesocc.org>

    oops borrado correctamente 

commit 43af71fcd7a71e468ebfa57d059f51bd5a9cacee 
Author: Mr. Floyd <mr.floyd@cshluesocc.org>

    commit accidental 

commit 22592c0f14990764a21437d792c07fadca50d24a 
Author: Mr. Floyd <mr.floyd@cshluesocc.org>

    oops elimiado del repositorio 

commit 812779449b6fb39450d1426899a39945b340fb19 
Author: Mr. Floyd <mr.floyd@cshluesocc.org>

    commit accidental 

commit e12b294a508bee8602943644c3e12a4c2f81583b 
Author: Mr. Floyd <mr.floyd@cshluesocc.org>

    README actualizado 
```

Conozcamos ahora otro útil comando __git mv__, es el análogo a mv en unix para mover y renombrar archivos y directorios. Según la documentación oficial: “Git no hace un seguimiento explicito del movimiento de archivos. Si renombras un archivo, en Git no se almacena ningún metadato que indique que lo has renombrado...”.
 
_«quedan dudas sobre eso, si sabes algo más no dudes en compartirlo acá...»_


Renombremos uno de nuestros archivos:

```
$ git mv script.py holaMundo.py 
$ git status 
# On branch master 
# Changes to be committed: 
#   (use "git reset HEAD <file>..." to unstage) 
# 
#	renamed:    script.py -> holaMundo.py

$ git commit -am "script.py renombrado a holaMundo.py" 
[master f3e2083] script.py renombrado a holaMundo.py 
 1 file changed, 0 insertions(+), 0 deletions(-) 
 rename script.py => holaMundo.py (100%) 
```

