# TAGGING

Cuando tenemos un historial de cambios lo suficientemente grande:

```
$ git log
commit fce0e7c556544fe200d78e563f7678cf5de7959f
Author: Carlos Cárcamo <carloscarcamo.m@gmail.com>
Date:   Mon Feb 23 23:17:32 2015 -0600

    Update revirtiendo_cambios.md

commit af00094f53070d509c6b92d95c2c0641e0d9abfd
Author: Carlos Cárcamo <carloscarcamo.m@gmail.com>
Date:   Mon Feb 23 23:14:59 2015 -0600

    Update ignorando_archivos.md

commit ebd2e359cf8977ffda7da37f10416b0c9c180029
Author: Carlos Cárcamo <carloscarcamo.m@gmail.com>
Date:   Mon Feb 23 23:11:55 2015 -0600

    Update git_basico.md

commit 1ad7986a2cffd13b7959d35735a7f9fcc16097fd
Author: Carlos Cárcamo <carloscarcamo.m@gmail.com>
Date:   Mon Feb 23 22:55:43 2015 -0600

    Update configuracion_inicial.md
:
```

Es posible empezar a tener problemas a buscar dentro de él, realizar cambios, o regresar a algún punto específico para realizar una ramificación.

Utilizamos las etiquetas (tag) para especificar eventos en nuestro historial que sean importantes, hacer versiones o delimitar lanzamientos.

Para mostrar las diferentes etiquetas que se han otorgado en nuestro repositorio ejecutamos:

```
$ git tag
v1.0.0
v2.0.0
```

Podemos crear puntos en cualquier cambio realizado, si queremos agregar uno en nuestro estado actual:

```
$ git tag -a v3.0.0 -m "Versión 3"
```

O si queremos agregarlo a un punto anterior, utilizamos el id del commit (completo o simplificado):

```
$ git tag -a v2.1.0 -m "Segundo release de la versión 2" af00094
```

Para buscar las subversiones o lanzamientos de alguna versión en específico, podemos listar:

```
$ git tag -l "v2.*"
v2.0.0
v2.1.0
```

O ver sus detalles (líneas y archivos modificados):

```
$ git show v2.1.0
tag v2.1.0
Tagger: agustin.rumayor <agustin.rumayor@gmail.com>
Date:   Tue Sep 20 10:46:12 2016 -0500

Segundo release de la versión 2

commit af00094f53070d509c6b92d95c2c0641e0d9abfd
Author: Carlos Cárcamo <carloscarcamo.m@gmail.com>
Date:   Mon Feb 23 23:14:59 2015 -0600

    Update ignorando_archivos.md

diff --git a/ignorando_archivos.md b/ignorando_archivos.md
index c2464f4..7ef17fc 100644
--- a/ignorando_archivos.md
+++ b/ignorando_archivos.md
```

Una herramienta que se vuelve esencial cuando nuestro repositorio se vuelve complejo es grep. El cual nos ayuda a buscar textos en nuestros archivos modificados en las diferentes versiones que hayamos publicado.
Ya sea alguna línea que hayamos borrado hace tiempo o buscar con expresiones regulares para hacer algún cambio en alguna versión:

```
$ git grep "comando" v2.0.0

v2.0.0:Pushing .md:Veamos ahora la salida del comando git status, __“Your branch is ahead of 'origin/master' by 1 commit.”__ nos indica que tenemos cambios en nuestro repositorio local que no han sido enviados al repositorio remoto. Podemos comprobar si tenemos diferencias entre nuestra repo local y la repo remota haciendo un diff así:
v2.0.0:clonando_repositorios.md:Comencemos entonces con la practica, copiemos el vinculo “clone url” y abramos una terminal y ejecutemos el comando clone:
:
```

