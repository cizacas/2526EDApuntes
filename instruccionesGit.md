# Instrucciones Git

`git init`: Esto crea un subdirectorio nuevo llamado .git, el cual contiene todos los archivos necesarios del repositorio – un esqueleto de un repositorio de Git. Todavía no hay nada en tu proyecto que esté bajo seguimiento.

`git clone <url_repositorio>`: Clona un repositorio remoto a tu máquina local.

`git fetch`: Descarga los cambios realizados en el repositorio remoto.

`git merge <nombre_rama>`: Impacta en la rama en la que te encuentras parado, los cambios realizados en la rama “nombre_rama”.

`git pull`: Unifica los comandos fetch y merge en un único comando.

`git commit -m "<mensaje>"`: Confirma los cambios realizados. El “mensaje” generalmente se usa para asociar al commit una breve descripción de los cambios realizados.

`git push origin <nombre_rama>`: Sube la rama “nombre_rama” al servidor remoto.

`git status`: Muestra el estado actual de la rama, como los cambios que hay sin commitear.

`git add <nombre_archivo>`: Comienza a trackear el archivo “nombre_archivo”.

## Comandos para trabajar con ramas

`git branch`: Lista todas las ramas locales del repositorio.

`git branch <nombre_rama>`: Crea una nueva rama con el nombre especificado, pero no cambia a ella.

`git branch -a`: Lista todas las ramas locales y remotas.

`git branch -d <nombre_rama>`: Elimina la rama local con el nombre "nombre_rama". Solo funciona si la rama ya ha sido fusionada.

`git branch -D <nombre_rama>`: Fuerza la eliminación de la rama local, incluso si no ha sido fusionada.

`git checkout <nombre_rama>`: Cambia a la rama especificada.

`git checkout -b <nombre_rama_nueva>`: Crea una rama a partir de la que te encuentres posicionado con el nombre "nombre_rama_nueva", y automáticamente cambia a la rama nueva.

`git checkout -t origin/<nombre_rama>`: Si existe una rama remota de nombre "nombre_rama", al ejecutar este comando se crea una rama local con el mismo nombre para hacer un seguimiento de la rama remota.

`git switch <nombre_rama>`: Comando moderno para cambiar entre ramas (alternativa a checkout).

`git switch -c <nombre_rama>`: Crea y cambia a una nueva rama (alternativa moderna a checkout -b).

## Comandos para fusionar ramas

`git merge <nombre_rama>`: Fusiona la rama especificada en la rama actual. Integra los cambios realizados en "nombre_rama" a la rama en la que estás posicionado.

`git merge --no-ff <nombre_rama>`: Fusiona la rama creando siempre un commit de merge, incluso si es posible hacer fast-forward.

`git merge --abort`: Cancela el proceso de fusión y vuelve al estado anterior si hay conflictos.

`git rebase <nombre_rama>`: Reorganiza los commits de la rama actual sobre la rama especificada. Alternativa al merge que mantiene un historial lineal.

`git push origin <nombre_rama>`: Commitea los cambios desde el branch local origin al branch “nombre_rama”.

`git remote prune origin`: Actualiza tu repositorio remoto en caso de que algún otro desarrollador haya eliminado alguna rama remota.

`git reset --hard HEAD`: Elimina los cambios realizados que aún no se hayan hecho commit.

`git revert <hash_commit>`: Revierte el commit realizado, identificado por el “hash_commit”.