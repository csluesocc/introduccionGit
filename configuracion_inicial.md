#CONFIGURACIÓN INICIAL

Lo primero que debemos hacer, luego de instalar git, es configurar nuestro nombre y email con el que git nos identificará cada vez que trabajemos sobre nuestros proyectos.

Git permite configurar varias opciones y solo es necesario hacerlo una vez, por el momento nos centraremos en lo básico, como siempre, recomendamos indagar un poco en la documentación oficial para más detalles.

El comando que usaremos para configurar nuestro entorno git sera: __git config__, que nos permiten definir variables de configuración.

Comencemos por decir a git quienes somos y cual es nuestro email, con esto git y demás usuarios sabrán quien ha hecho cambios (commits).

```shell
$ git config --global user.name "Mr. Floyd"
$ git config --global user.email mr.floyd@ues.edu.sv
```

con __--global__ estas diciendo a git que use esta información en todo lo que hagas en el sistema.

Puedes ver tu configuración actual ejecutando:

```shell
$ git config --list 
user.name= Mr. Floyd
user.email=mr.floyd@cshluesocc.org
```

puedes además preguntar a git por parámetros específicos definidos en tu configuración:

```shell
$ git config user.email
mr.floyd@cshluesocc.org
```

Si necesitas una lista completa de los comandos usados en git puedes ejecutar en tu terminal:

```shell
$ git help
```

o bien consultar por un comando específico con __git help «comando»__:

```shell
$ git help config
```

o como usualmente lo hacemos en GNU/Linux usando __'man'__

```shell
$ man git-config
```























