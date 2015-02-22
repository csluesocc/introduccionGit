# INSTALACIÓN

_Para poder seguir este tutorial, lo único que necesitarás sera una distro GNU/Linux, una terminal para ejecutar un par de comandos y sobre todo muchas granas de aprender e investigar._

##INSTALANDO GIT EN TU DISTRO FAVORITA

La forma más sencilla de instalar git en nuestro ordenador es utilizado el gestor de paquetes de nuestra distro favorita e instalar git desde sus repositorios, git seguramente esta en los repositorios de las distros más conocidas por lo que vamos a proceder de la siguiente manera:

###Fedora, CentOS  y derivados: 
```shell
# yum install git-core
```
o bien con: 

```shell
$ sudo yum install git-core
```

nota: si “git-core” no existe en los repositorios utilizar “git” en su lugar.

###Debian y derivados:

```shell
# apt-get install git
```

o

```shell
$ sudo apt-get install git
```
###Arch linux y derivados:

```shell
# pacman -S git
```

o también con:

```shell
$ sudo pacman -S git
```

Si tu distro no esta entre las mencionadas, visita la documentación de tu distro, seguramente encontraras los pasos necesarios para instalar git en tu sistema favorito. 

La opción alternativa a usar el gestor de paquetes es compilar el código fuente nosotros mismos.
Si quieres compilar el código fuente puedes buscar en el siguiente enlace los pasos a seguir: http://git-scm.com/book/en/Getting-Started-Installing-Git.

