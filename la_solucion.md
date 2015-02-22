# LA SOLUCIÓN

##LOS SISTEMAS DE CONTROL DE VERSIONES AL RESCATE

La penosa situación anterior llevo a la necesidad de crear un sistema capaz de realizar las tareas anteriores de forma ordenada, concisa y sobre todo eficiente, pudiendo centralizar el trabajo en un lugar especifico, un servidor, a este tipo de sistemas se les llama sistemas de control de versiones centralizados (como apache subversión) con esto se tiene un lugar donde mantener las versiones, pero aun existe un problema, ¿Y si el servidor colapsa? Se pierde todo!.
Tampoco suena muy eficiente, entonces que necesitamos? La respuesta es sencilla, necesitamos un sistema de control de versiones distribuidos.
En los sistemas de control de versiones distribuidos (ejemplos: Git, Mercurial, entre otros), los clientes no sólo descargan la última versión de los archivos, la replican completamente en sus computadoras. Así, si un servidor colapsa, cualquiera de los repositorios de los clientes puede copiarse en el servidor para restaurarlo (es lo mismo que tener una copia de seguridad completa de los datos). 

Ahora en día con servicios como los de [github](https://github.com/), [bitbucket](https://bitbucket.org/), entre otros, mantener un proyecto es mas fácil y nos ahorramos la necesidad de tener un servidor dedicado para mantener el proyecto al alcance de todos, además los usuarios pueden acceder a los repositorios desde cualquier lugar con una conexión a internet.

Lo anterior fue una breve reseña de lo que son los sistemas de control de versiones y del porque deberíamos usarlos.

A continuación nos centraremos en utilizar y poner en practica uno de los sistemas de control de versionas (SVC por sus siglas en ingles) más utilizados en el mundo, hablamos de __git__, creado por __Linus Torvalds__ el mismo creador el Kernel Linux y por la comunidad que trabaja en el mismo kernel.

