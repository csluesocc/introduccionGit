# RAMIFICACIONES

La ramificación es uno de los mecanismos más interesantes y usados en los sistemas de control de versiones modernos, al hablar de ramificaciones, hablamos que hemos tomado la rama principal de desarrollo (master) y a partir de ella hemos continuado trabajando sin seguir la rama principal de desarrollo, es decir en una rama diferente.

Un ejemplo de esto podría ser el desarrollo del sistema operativo universal GNU/debian, el equipo de debian mantiene siempre tres versiones de su sistema, el estable, en pruebas y de desarrollo (actualmente estas ramas son wheezy, jessie y sid) . La __rama estable__ es donde los paquetes han sido probados y están listos para salir al mundo con un minino o nulos bugs, en la __rama en pruebas__ sin embargo es donde se mantienen los paquetes más actualizados pero que aun no ha superado la fase de pruebas para salir al mundo e integrarse a la rama estable, mientras que la __rama de desarrollo__ están los paquetes, módulos del sistema, etc. que aun no están listos para producción y que están cambiando constantemente y que pueden terminar agregándose o ser eliminados en cualquier momento. 

Procedamos entonces a crear nuestra primera ramificación, actualmente ya estamos trabajando bajo una rama y es la rama master que por defecto git nos crea y que es donde hemos estado realizando los cambios, así que crearemos una rama nueva, cabe mencionar que al crear una rama a partir de otra, la nueva rama contiene, inicialmente, los mismos archivos y commits que la rama base, hasta que modifiquemos o agreguemos nuevos archivos y directorios.

```
$ git branch testing 
$ git status
# On branch master 
nothing to commit (working directory clean)
```

Al parecer no hemos hecho nada, pero hemos creado una rama nueva llamada testing, para ver que esto es cierto ejecutemos:

```
$ git branch
* master 
  testing
```
  
  
  
  
  
  
  
  
  