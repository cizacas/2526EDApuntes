# UD3: Control de versiones

- [UD3: Control de versiones](#ud3-control-de-versiones)
  - [1. ¿Qué es el control de versiones?](#1-qué-es-el-control-de-versiones)
  - [2. Control de versiones en Java](#2-control-de-versiones-en-java)
  - [3. Git](#3-git)
    - [3.1 Arquitectura de Git](#31-arquitectura-de-git)
    - [3.2. Flujo de trabajo en Git](#32-flujo-de-trabajo-en-git)
    - [3.3. Git con repositorios remotos](#33-git-con-repositorios-remotos)
    - [3.4. Ramas en Git (Branches)](#34-ramas-en-git-branches)
      - [3.4.1. ¿Qué son las ramas y por qué se crean?](#341-qué-son-las-ramas-y-por-qué-se-crean)
      - [3.4.2. Finalidad de las ramas](#342-finalidad-de-las-ramas)
      - [3.4.3. Tipos de ramas comunes](#343-tipos-de-ramas-comunes)
      - [3.4.4. Crear y gestionar ramas](#344-crear-y-gestionar-ramas)
      - [3.4.5. Fusionar ramas (Merge)](#345-fusionar-ramas-merge)
      - [3.4.6. Tipos de fusión](#346-tipos-de-fusión)
      - [3.4.7. Conflictos de fusión](#347-conflictos-de-fusión)
      - [3.4.8. Buenas prácticas con ramas](#348-buenas-prácticas-con-ramas)
    - [3.5. Principales instrucciones de Git](#35-principales-instrucciones-de-git)
  - [4. GitHub](#4-github)

## 1. ¿Qué es el control de versiones?
Se llama __control de versiones__ a la gestión de los diversos cambios que se realizan sobre los elementos de algún producto o una configuración del mismo. Una versión, revisión o edición de un producto, es el estado en el que se encuentra el mismo en un momento dado de su desarrollo o modificación.

Aunque un sistema de control de versiones puede realizarse de forma manual, es muy aconsejable disponer de herramientas que faciliten esta gestión dando lugar a los llamados __sistemas de control de versiones__ o VCS (del inglés Version Control System). Estos sistemas facilitan la administración de las distintas versiones de cada producto desarrollado, así como las posibles especializaciones realizadas (por ejemplo, para algún cliente específico). Ejemplos de este tipo de herramientas son entre otros: CVS, Subversion, SourceSafe, ClearCase, Darcs, Bazaar, Plastic SCM, Git, SCCS, Mercurial, Perforce, Fossil SCM, Team Foundation Server.

Dentro de los VCS encontramos dos arquitecturas dependiendo de como se organice.
- __Arquitectura centralizada o cliente-servidor__: Un único servidor contiene todos los archivos versionados, y varios clientes acceden a este servidor para obtener y actualizar los archivos.

  Cuenta con un repositorio central al que se accede mediante un cliente en su máquina. Tiene un único servidor que contiene todos los archivos versionados, y varios clientes que descargan los archivos desde ese lugar central.

![arquitectura centralizada](img/arquitectura_centralizada.jpg)

- __Arquitectura distribuida__: Cada usuario tiene una copia completa del repositorio. Esto significa que, si el servidor principal se pierde, cualquier usuario puede restaurarlo a partir de su copia.

  Cada usuario tiene su propio repositorio, por ello, cada vez que se descarga una versión del proyecto se hace una copia de seguridad completa de todos los datos. 
Así, si un servidor muere, cualquiera de los repositorios de los usuarios puede copiarse en el servidor para restaurarlo.
    
![](img/arquitectura_distribuida.jpg)

## 2. Control de versiones en Java
En los proyectos Java existen varios sistemas principales de control de versiones de código abierto:
- __CVS__ es una herramienta de código abierto que es usada por gran cantidad de organizaciones. 
- __Subversion__ es el sucesor natural de CVS, ya que se adapta mejor que CVS a las modernas prácticas de desarrollo de software. 
- __Git__ es un software de control de versiones diseñado pensando en la eficiencia, la confiabilidad y compatibilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran número de archivos de código fuente. Profundizaremos en el resto de la unidad.

## 3. Git
Git es un sistema de control de versiones distribuido, gratuito y de código abierto, diseñado para manejar proyectos de cualquier tamaño con rapidez y eficiencia. Es fácil de aprender, ocupa poco espacio y tiene un rendimiento superior a herramientas como Subversion o CVS.

![logo git](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Git-logo.svg/1024px-Git-logo.svg.png)

### 3.1 Arquitectura de Git
Aunque Git es un sistema distribuido, puede comportarse de manera centralizada al trabajar con un servidor remoto. Git organiza los archivos en tres estados:

- **Committed** (confirmado): Los datos están guardados de forma segura en el repositorio local.
- **Modified** (modificado): Los archivos se han modificado pero aún no se han preparado para el commit.
- **Staged** (preparado): Los cambios se han marcado para ser confirmados en el próximo commit.

Las tres áreas principales de un proyecto de Git son:

- **Git directory** (directorio de Git): Base de datos de objetos y metadatos. Aquí se almacenan las versiones confirmadas.
- **Working directory** (directorio de trabajo): Área donde editas los archivos. Proviene de una versión descomprimida del repositorio.
- **Staging area** (área de preparación): Espacio donde se preparan los archivos antes de confirmarlos.

![git local](img/Git_local.jpg)

Puedes encontrar toda la documentación sobre git en su web [git-scm.com](https://git-scm.com/)

### 3.2. Flujo de trabajo en Git

El flujo de trabajo en Git se basa en:
1. Modificar los archivos en el Directorio de Trabajo.
2. Preparar los archivos para el commit añadiéndolos al Área de Preparación.
3. Confirmar los cambios, guardando las instantáneas en el repositorio.

Los tres estados en los que se pueden encontrar un archivo en Git son:
- __Commited__ (confirmado): Los datos están almacenados de forma segura en el repositorio local.
- __Modified__ (modificado): Has cambiado el archivo, pero no lo has confirmado en el repositorio.
- __Staged__ (preparado): Has marcado un archivo modificado en su versión actual para que vaya en el próximo commit o confirmación que hagas.

Esto nos lleva a las tres secciones principales de un proyecto de Git serán:
- __Git directory__ (directorio de Git). Contiene base datos objetos y metadatos del proyecto. Es la parte más importante de Git, es lo que copiamos cuando clonamos el repositorio desde otro ordenador.
- __Working directory__ (directorio de trabajo). Es una copia de una versión del proyecto para poder trabajar. Estos archivos se obtienen de la base de datos comprimida en el Git Directory y se guardan en nuestro equipo local para poder editarlos.
- __Staging area__ (área de preparación o índice). Es un archivo que está en nuestro directorio de Git y almacena la información sobre lo que va a ir en la próxima confirmación. 

![Git](img/git1.png)

Por lo que podemos decir que:
- Las versiones de los archivos que están en el Directorio de Git se consideran Commited (confirmadas).
- Si la versión ha sufrido cambios desde que se obtuvo el repositorio y han sido añadidas al Área de Preparación, se considera Staged (preparada).
- Si los cambios no se han añadido al Área de preparación, está Modified (modificada).

### 3.3. Git con repositorios remotos

Para trabajar con un repositorio remoto es necesario conocer varios conceptos:
- __Origin__: nombre por defecto del repositorio remoto principal.
- __Master /Main__: nombre de la rama principal que se crea por defecto.
- __Head__: El commit en el que está el repositorio actualmente, suele ser el último commit de la rama principal.

![git remoto](img/Git_remoto.jpg)

### 3.4. Ramas en Git (Branches)

#### 3.4.1. ¿Qué son las ramas y por qué se crean?

Una **rama** (branch) en Git es una línea independiente de desarrollo que permite trabajar en diferentes versiones del proyecto de forma simultánea. Las ramas son una de las características más potentes de Git.

**Razones principales para crear ramas:**

1. **Desarrollo de nuevas funcionalidades**: Permite trabajar en una nueva característica sin afectar al código estable de la rama principal.
2. **Corrección de errores**: Se pueden crear ramas específicas para solucionar bugs sin interferir con el desarrollo de otras funcionalidades.
3. **Experimentación**: Probar nuevas ideas sin riesgo de romper el código funcional.
4. **Trabajo en equipo**: Varios desarrolladores pueden trabajar en paralelo en diferentes tareas sin generar conflictos.
5. **Versiones de producción**: Mantener diferentes versiones del software (desarrollo, pruebas, producción).

#### 3.4.2. Finalidad de las ramas

Las ramas permiten:
- **Aislamiento**: Los cambios en una rama no afectan a otras ramas hasta que se fusionen.
- **Organización**: Mantener el código organizado según características, versiones o entornos.
- **Colaboración**: Facilitar el trabajo en equipo sin interferencias.
- **Reversibilidad**: Si una rama no funciona como se esperaba, se puede eliminar sin afectar al resto del proyecto.

#### 3.4.3. Tipos de ramas comunes

- **main/master**: Rama principal que contiene el código estable y en producción.
- **develop**: Rama de desarrollo donde se integran las nuevas funcionalidades.
- **feature/**: Ramas para desarrollar nuevas características (ej: `feature/login`, `feature/carrito-compra`).
- **hotfix/**: Ramas para correcciones urgentes en producción.
- **release/**: Ramas para preparar nuevas versiones.

#### 3.4.4. Crear y gestionar ramas

**Crear una nueva rama:**
```bash
git branch nombre-rama
```

**Cambiar a una rama:**
```bash
git checkout nombre-rama
```

**Crear y cambiar a una rama nueva (en un solo comando):**
```bash
git checkout -b nombre-rama
```

**Ver todas las ramas:**
```bash
git branch        # ramas locales
git branch -a     # ramas locales y remotas
```

**Eliminar una rama:**
```bash
git branch -d nombre-rama
```

#### 3.4.5. Fusionar ramas (Merge)

La **fusión** (merge) es el proceso de integrar los cambios de una rama en otra. Es fundamental para incorporar las nuevas funcionalidades o correcciones a la rama principal.

**Proceso de fusión:**

1. **Posicionarse en la rama destino** (donde queremos traer los cambios):
   ```bash
   git checkout main
   ```

2. **Fusionar la rama origen** (la que contiene los cambios):
   ```bash
   git merge nombre-rama
   ```

**Ejemplo práctico:**
```bash
# Crear una rama para una nueva funcionalidad
git checkout -b feature/nueva-funcionalidad

# Realizar cambios y commits
git add .
git commit -m "Añadida nueva funcionalidad"

# Volver a la rama principal
git checkout main

# Fusionar los cambios
git merge feature/nueva-funcionalidad

# Eliminar la rama si ya no se necesita
git branch -d feature/nueva-funcionalidad
```

#### 3.4.6. Tipos de fusión

**Fast-forward**: Cuando no hay commits nuevos en la rama destino, Git simplemente mueve el puntero hacia adelante.

```
Antes:      main: A---B
                       \
            feature:    C---D

Después:    main: A---B---C---D
```

**Three-way merge**: Cuando ambas ramas tienen commits diferentes, Git crea un nuevo commit de fusión.

```
Antes:      main:    A---B---E
                          \
            feature:       C---D

Después:    main:    A---B---E---F (commit de merge)
                          \     /
            feature:       C---D
```

#### 3.4.7. Conflictos de fusión

Cuando dos ramas modifican las mismas líneas de un archivo, Git no puede fusionarlas automáticamente y genera un **conflicto**.

**Pasos para resolver conflictos:**

1. Git marca los archivos en conflicto:
   ```bash
   git status  # Ver archivos con conflictos
   ```

2. Abrir los archivos y buscar las marcas de conflicto:
   ```
   <<<<<<< HEAD
   Código de la rama actual
   =======
   Código de la rama a fusionar
   >>>>>>> nombre-rama
   ```

3. Editar manualmente el archivo, eligiendo qué cambios conservar.

4. Eliminar las marcas de conflicto (`<<<<<<<`, `=======`, `>>>>>>>`).

5. Añadir el archivo resuelto:
   ```bash
   git add archivo-resuelto
   ```

6. Completar la fusión:
   ```bash
   git commit -m "Resueltos conflictos de fusión"
   ```

#### 3.4.8. Buenas prácticas con ramas

- Usar nombres descriptivos para las ramas (`feature/login`, `bugfix/error-calculo`).
- Mantener las ramas pequeñas y enfocadas en una única tarea.
- Fusionar regularmente los cambios de la rama principal a tu rama de trabajo para evitar conflictos grandes.
- Eliminar las ramas una vez fusionadas para mantener el repositorio limpio.
- Hacer commits frecuentes y con mensajes claros.
- Sincronizar con el repositorio remoto regularmente.

### 3.5. Principales instrucciones de Git

Los principales comandos de Git son los siguientes:

![instrucciones git](img/git.png)

- **checkout**: Cambiar entre ramas o actualizar el directorio de trabajo.
- **clone**: Clonar un repositorio remoto en tu máquina local.
- **add**: Añadir archivos modificados o nuevos al área de preparación.
- **commit**: Guardar los cambios preparados en el repositorio.
- **fetch**: Obtener cambios desde el repositorio remoto, sin fusionarlos.
- **pull**: Traer y fusionar cambios del repositorio remoto.
- **push**: Enviar cambios al repositorio remoto.

Puedes encontrar los comandos explicados con más detalle en el siguiente enlace: [instrucciones Git](instruccionesGit.md)

Para ampliar información y consolidar conceptos sobre Git es recomendable acudir a la documentación oficial ([git-scm.com](https://git-scm.com/)) y al libro de Git ([GitBook](https://git-scm.com/book/es/v2)).

## 4. GitHub
GitHub es una plataforma de desarrollo colaborativo para alojar proyectos utilizando el sistema de control de versiones Git. Se utiliza principalmente para el desarrollo de software. El código de los proyectos alojados en GitHub se almacena generalmente de forma pública.

![logo github](img/GitHub.png)

El objetivo de GitHub es facilitar el trabajo colaborativo, que es aquel en el cual un grupo de personas intervienen aportando sus ideas y conocimientos con el objetivo de lograr una meta común.
El grupo puede ser desde un reducido equipo de trabajo para un proyecto empresarial o académico hasta grupos inmensos que colaboran en proyectos masivos.

Ver vídeo explicativo del funcionamiento de GitHub: [What is GitHub?](https://www.youtube.com/watch?v=w3jLJU7DT5E)

Puedes consultar más información sobre GitHub en su web [github.com](https://github.com/)

:pencil: Actividades 2 y 3