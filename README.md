
Practicas EGC Git
===================


Proyecto de demostración de uso del flujo de trabajo con la herramienta git para las prácticas de la asignatura EGC.

El objetivo de la creación de este proyecto es aprender a manejar git como control de código, trabajando con diferentes ramas y sabiendo resolver conflictos.

----------
Desarrollo
-------------
Se crea un repositorio  local - remoto:

    $git init
    $git add README.md
    $git commit -m "Primer commit"
    $git remote add origin https://github.com/alegargar/egcgit.git
    $git push -u origin master

Trabajando en la rama *master* se crea y se añade un fichero html con una estructura básica

Seguidamente se crea una rama *feature* y se comienza a trabajar en ella:

    $git branch feature
    $git  checkout feature

Se realizan modificaciones en el fichero, y se sube la rama a remoto

    $git  push origin feature:feature

Con *feature:feature* indicamos que la rama local feature la suba a una rama remota feature

Tras realizar las modificaciones necesarias volvemos a la rama master

    $git  checkout master
Ahora, para forzar el conflicto, realizamos las mismas modificaciones, pero esta vez, cambiando el nombre de la función.
Subimos los cambios y luego unimos las ramas

    $git merge feature
Obteniendo un error que indica la existencia de conflictos. Aunque realizarse el proceso inverso para indicar con una nueva instrucción que se resolviera automáticamente de varias formas

    # Por ejemplo, esto indicaría que se quedara con la rama que está uniendo
    # y desechara el codigo de la rama actual

    $git merge -s recursive -X theirs feature

Aprovechamos la funcionalidad de git que marca las líneas conflictivas de código dejando constancia de las diferencias de ambas versiones de código, para revisarlo personalmente y elegir la correcta tal y como haríamos en la mayoría de situaciones reales

    <<<<<<< HEAD
        function operando(){
    =======
        function opera(){
    >>>>>>> feature
Con lo anterior git indica el contenido de cada rama.
Solucionamos los conflictos manualmente, y procedemos a subir los cambios
