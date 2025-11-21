#### ED - 1ºCFGS DAM <img src="img/logo.jpg" style="float: right; width: 180px; height: 46px">
<div style="text-align: center;"><strong>Unidad 3 - Actividad 3</strong></div>

---

# Ejercicio Práctico: Trabajo en Equipo con Git, NetBeans y GitHub

## Descripción del ejercicio

Este ejercicio simula un escenario real de desarrollo colaborativo en equipo utilizando Git, NetBeans y GitHub. Tres desarrolladores trabajarán simultáneamente en diferentes funcionalidades de un proyecto Java, cada uno en su propia rama, y realizarán las fusiones en el repositorio remoto (GitHub).

## Objetivos de aprendizaje

- Trabajar con ramas individuales para cada desarrollador
- Realizar commits y push desde NetBeans
- Fusionar cambios en el repositorio remoto (GitHub)
- Resolver conflictos de fusión
- Aplicar buenas prácticas de trabajo colaborativo

## Equipo de trabajo

**Equipo de 3 personas:**
- **Desarrollador A** (Líder/Coordinador): Responsable del proyecto base y la integración
- **Desarrollador B**: Desarrollo de funcionalidades específicas
- **Desarrollador C**: Desarrollo de funcionalidades específicas

## Proyecto: Calculadora Básica

Crearán una aplicación Java simple con operaciones matemáticas básicas. El proyecto tendrá:
- `Calculadora.java` - Programa principal
- Cada desarrollador añadirá operaciones diferentes

## Fase 1: Preparación inicial (Desarrollador A - Líder)

### Paso 1.1: Crear el repositorio en GitHub

1. Iniciar sesión en GitHub
2. Crear un nuevo repositorio:
   - Nombre: `CalculadoraEquipo`
   - Descripción: "Calculadora básica - Ejercicio colaborativo"
   - Visibilidad: Público o Privado (según preferencia)
   - ✅ Inicializar con README
   - Añadir `.gitignore` para Java
3. Copiar la URL del repositorio (HTTPS o SSH)

### Paso 1.2: Configurar el proyecto en NetBeans

1. Abrir NetBeans
2. Crear nuevo proyecto:
   - File → New Project → Java → Java Application
   - Project Name: `CalculadoraEquipo`
   - Ubicación: Elegir una carpeta local
   - Create Main Class: `calculadora.Calculadora`

### Paso 1.3: Clonar y conectar con GitHub

**Inicializar Git en el proyecto existente en NetBeans**

1. Clic derecho en el proyecto → Versioning → Initialize Git Repository
2. Seleccionar la carpeta del proyecto → OK
3. Añadir el repositorio remoto desde NetBeans:
   - Clic derecho en el proyecto → Git → Remote → Add
   - Name: `origin`
   - URL: `https://github.com/usuario/CalculadoraEquipo.git`
   - Click en **Add**
4. Traer el contenido inicial del remoto:
   - Hacer el pull desde NetBeans: Git → Remote → Pull, seleccionar `origin/main`

### Paso 1.4: Crear estructura base del proyecto

Crear el archivo `Calculadora.java` con el código base:

```java
package calculadora;

import java.util.Scanner;

public class Calculadora {
    public static void main(String[] args) {
        System.out.println("=== Calculadora Básica ===");
        System.out.println("Versión 1.0");
        // Las operaciones serán implementadas por el equipo
    }
}
```

### Paso 1.5: Realizar el primer commit y push

En NetBeans:
1. Clic derecho en el proyecto → Git → Commit
2. Seleccionar todos los archivos
3. Mensaje: "Estructura inicial del proyecto"
4. Commit y Push
5. Seleccionar la rama `main`
6. Push

### Paso 1.6: Invitar a los colaboradores

En GitHub:
1. Ir a Settings → Collaborators
2. Añadir los usuarios de GitHub de los Desarrolladores B y C
3. Los desarrolladores deben aceptar la invitación por email

## Fase 2: Configuración individual (Todos los desarrolladores)

### Paso 2.1: Clonar el repositorio (Desarrolladores B y C)

1. Aceptar la invitación al repositorio
2. En NetBeans:
   - Team → Git → Clone
   - Repository URL: URL del repositorio de GitHub
   - User/Password: Credenciales de GitHub
   - Seleccionar carpeta de destino
   - Clone

### Paso 2.2: Crear ramas individuales

**Cada desarrollador crea su propia rama desde NetBeans:**

1. Clic derecho en el proyecto → Git → Branch/Tag → Create Branch
2. Nombres de ramas:
   - Desarrollador A: `feature/suma-resta`
   - Desarrollador B: `feature/multiplicacion-division`
   - Desarrollador C: `feature/menu`
3. Crear la rama
3. Comprobar que estas en la nueva rama, verifícalo con "Switch to New Branch"

**Verificar rama actual:**
- En el nombre del proyecto aparece entre paréntesis el nombre de la rama actual

### Paso 2.3: Publicar la rama en GitHub

Después de crear la rama local, necesitas subirla al repositorio remoto:

**Opción 1: Push to Upstream (recomendado para nueva rama)**
1. Clic derecho en el proyecto → Git → Remote → Push to Upstream
2. Esto creará automáticamente la rama en GitHub con el mismo nombre y establecerá el seguimiento

**Opción 2: Push (cuando ya existe conexión)**
1. Clic derecho en el proyecto → Git → Remote → Push
2. Seleccionar la rama remota de destino

**Diferencia entre Push to Upstream y Push:**
- **Push to Upstream**: Sube la rama local al remoto Y establece la conexión de seguimiento (upstream). Es ideal la primera vez que publicas una rama nueva. Git recordará que tu rama local `feature/suma-resta` corresponde a `origin/feature/suma-resta`.
- **Push**: Solo sube los cambios. Debes especificar manualmente a qué rama remota enviar. Se usa cuando ya existe la rama en el remoto y el seguimiento está configurado.

> **Consejo**: La primera vez que subes una rama nueva, usa siempre **Push to Upstream**. Las siguientes veces puedes usar simplemente **Push**.

## Fase 3: Desarrollo paralelo

### Tarea del Desarrollador A: Suma y Resta
**Rama: `feature/suma-resta`**

Modificar `Calculadora.java` añadiendo las funciones de suma y resta:

```java
package calculadora;

import java.util.Scanner;

public class Calculadora {
    
    public static void main(String[] args) {
        System.out.println("=== Calculadora Básica ===");
        System.out.println("Versión 1.0");
        
        // Ejemplo de uso de suma y resta
        System.out.println("\nEjemplos de operaciones:");
        System.out.println("5 + 3 = " + sumar(5, 3));
        System.out.println("10 - 4 = " + restar(10, 4));
    }
    
    // Función para sumar dos números
    public static double sumar(double num1, double num2) {
        return num1 + num2;
    }
    
    // Función para restar dos números
    public static double restar(double num1, double num2) {
        return num1 - num2;
    }
}
```

**Commit y Push:**
1. Git → Commit
2. Mensaje: "Añadidas funciones de suma y resta"
3. Commit y Push
4. Push to: `origin/feature/suma-resta`

### Tarea del Desarrollador B: Multiplicación y División
**Rama: `feature/multiplicacion-division`**

Modificar `Calculadora.java` añadiendo las funciones de multiplicación y división:

```java
package calculadora;

import java.util.Scanner;

public class Calculadora {
    
    public static void main(String[] args) {
        System.out.println("=== Calculadora Básica ===");
        System.out.println("Versión 1.0");
        
        // Ejemplo de uso de multiplicación y división
        System.out.println("\nEjemplos de operaciones:");
        System.out.println("6 * 4 = " + multiplicar(6, 4));
        System.out.println("20 / 5 = " + dividir(20, 5));
    }
    
    // Función para multiplicar dos números
    public static double multiplicar(double num1, double num2) {
        return num1 * num2;
    }
    
    // Función para dividir dos números
    public static double dividir(double num1, double num2) {
        if (num2 != 0) {
            return num1 / num2;
        } else {
            System.out.println("Error: No se puede dividir entre cero");
            return 0;
        }
    }
}
```

**Commit y Push:**
1. Git → Commit
2. Mensaje: "Añadidas funciones de multiplicación y división"
3. Commit y Push
4. Push to: `origin/feature/multiplicacion-division`

### Tarea del Desarrollador C: Menú Interactivo
**Rama: `feature/menu`**

Modificar `Calculadora.java` añadiendo un menú interactivo que use las funciones:

```java
package calculadora;

import java.util.Scanner;

public class Calculadora {
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int opcion;
        double num1, num2, resultado;
        
        do {
            System.out.println("\n=== Calculadora Básica ===");
            System.out.println("1. Sumar");
            System.out.println("2. Restar");
            System.out.println("3. Multiplicar");
            System.out.println("4. Dividir");
            System.out.println("0. Salir");
            System.out.print("Seleccione una opción: ");
            opcion = scanner.nextInt();
            
            if (opcion >= 1 && opcion <= 4) {
                System.out.print("Ingrese el primer número: ");
                num1 = scanner.nextDouble();
                System.out.print("Ingrese el segundo número: ");
                num2 = scanner.nextDouble();
                
                switch(opcion) {
                    case 1 -> System.out.println("Resultado: " + num1 + " + " + num2 + " = " + (num1 + num2));
                    case 2 -> System.out.println("Resultado: " + num1 + " - " + num2 + " = " + (num1 - num2));
                    case 3 -> System.out.println("Resultado: " + num1 + " * " + num2 + " = " + (num1 * num2));
                    case 4 -> {
                        if (num2 != 0) {
                            System.out.println("Resultado: " + num1 + " / " + num2 + " = " + (num1 / num2));
                        } else {
                            System.out.println("Error: No se puede dividir entre cero");
                        }
                    }
                }
            } else if (opcion == 0) {
                System.out.println("¡Hasta pronto!");
            } else {
                System.out.println("Opción no válida");
            }
        } while(opcion != 0);
        
        scanner.close();
    }
}
```

**Commit y Push:**
1. Git → Commit
2. Mensaje: "Añadido menú interactivo para la calculadora"
3. Commit y Push
4. Push to: `origin/feature/menu`

## Fase 4: Integración en GitHub (Pull Requests)

### ¿Por qué fusionar en el repositorio remoto?

**Ventajas de fusionar en GitHub (remoto):**
- ✅ **Revisión de código**: Otros pueden revisar antes de integrar
- ✅ **Documentación**: Queda registro de quién revisó y aprobó
- ✅ **Detección de conflictos**: GitHub avisa antes de fusionar
- ✅ **Seguridad**: La rama principal está protegida
- ✅ **Trazabilidad**: Historial claro de cambios

### Paso 4.1: Crear Pull Requests (Cada desarrollador)

**En GitHub (navegador web):**

1. Ir al repositorio en GitHub
2. Aparecerá un mensaje: "Your recently pushed branches"
3. Click en **"Compare & pull request"** para tu rama
4. Rellenar la Pull Request:
   - **Title**: Descripción clara (ej: "Añadir suma y resta")
   - **Description**: Detalles de los cambios realizados
   - **Reviewers**: Asignar al **Desarrollador A (Líder)** para revisión y aprobación
   - **Assignees**: Asignarte a ti mismo
5. Click en **"Create pull request"**

> **Nota**: Como el Desarrollador A será quien fusione las ramas, es lógico que también sea el revisor de las Pull Requests de los Desarrolladores B y C.

**Formato recomendado para la descripción:**
```
## Cambios realizados
- Añadidas funciones de suma y resta
- Funciones probadas con valores de ejemplo

## Archivos modificados
- `Calculadora.java`

## Testing
- [ ] Código compila sin errores
- [ ] Funciones probadas con diferentes valores
```

### Paso 4.2: Revisión de código (Desarrollador A - Líder)

El **Desarrollador A** como líder y revisor debe:
1. Ir a la pestaña **"Pull requests"**
2. Abrir cada PR asignada (de Desarrollador B y C)
3. Revisar los cambios en **"Files changed"**
4. Añadir comentarios si hay sugerencias de mejora
5. Si todo está correcto: **"Review changes"** → **"Approve"**

> **Flujo completo**: Desarrolladores B y C crean PR → Desarrollador A revisa → Desarrollador A aprueba → Desarrollador A fusiona

### Paso 4.3: Fusionar Pull Requests (Desarrollador A - Líder)

**Orden recomendado de fusión:**
1. Primero: `feature/suma-resta`
2. Segundo: `feature/multiplicacion-division`
3. Tercero: `feature/menu`

**Para cada Pull Request:**
1. Verificar que no hay conflictos
2. Click en **"Merge pull request"**
3. Confirmar el merge
4. Opcionalmente: **"Delete branch"** (eliminar rama remota)

### Paso 4.4: Actualizar repositorio local (Todos)

**Después de cada fusión, todos deben actualizar desde NetBeans:**

1. Cambiar a la rama main:
   - Git → Branch → Switch to Branch → `main`
2. Obtener cambios:
   - Git → Remote → Pull from Upstream (si es la primera vez o necesitas configurar el seguimiento)
   - O: Git → Remote → Pull (si ya tienes configurado el upstream)

**Diferencia entre Pull from Upstream y Pull:**
- **Pull from Upstream**: Descarga los cambios desde la rama remota configurada automáticamente (origin/main). No necesitas especificar de dónde traer los cambios.
- **Pull**: Descarga los cambios, pero si no tienes configurado el upstream, te pedirá que especifiques manualmente la rama remota.

> **Nota**: Si hiciste `Push to Upstream` al publicar la rama, el `Pull` simple funcionará perfectamente porque el seguimiento ya está establecido.

**En terminal (alternativa):**
```bash
git checkout main
git pull origin main
```

## Fase 5: Manejo de conflictos (Simulación)

### Crear un conflicto intencionado

Para practicar resolución de conflictos:

**Desarrollador B y C modificarán el mismo archivo simultáneamente:**

1. Ambos cambiar a rama `main` actualizada
2. Ambos crear nuevas ramas:
   - Dev B: `feature/readme-B`
   - Dev C: `feature/readme-C`
3. Ambos modificar `README.md` **en las mismas líneas**
4. Ambos hacer commit y push
5. Uno crea PR y fusiona primero (ej: Dev B)
6. El otro crea PR → **Aparecerá conflicto**

### Resolver el conflicto

**Desarrollador C (quien tiene el conflicto):**

**Opción 1: Resolver en GitHub (conflictos simples)**
1. En la PR, click en **"Resolve conflicts"**
2. Editar el archivo, elegir qué cambios mantener
3. Eliminar las marcas: `<<<<<<<`, `=======`, `>>>>>>>`
4. Click en **"Mark as resolved"**
5. **"Commit merge"**

**Opción 2: Resolver localmente en NetBeans (conflictos complejos)**

1. Asegurarse de estar en la rama con conflicto:
   - Git → Branch → Switch to Branch → `feature/readme-C`
2. Traer los cambios de main a tu rama:
   - Git → Remote → Pull from Upstream
   - En el diálogo, seleccionar `origin/main` como rama a fusionar
   - Esto intentará fusionar main en tu rama y mostrará los conflictos
3. NetBeans mostrará los archivos en conflicto (icono rojo con símbolo de conflicto)
4. Clic derecho en el archivo en conflicto → Git → Resolve Conflicts
5. Se abre el editor de conflictos de NetBeans:
   - **Left** (izquierda): Tu versión (feature/readme-C)
   - **Right** (derecha): Versión de main
   - **Result** (abajo): Resultado final que puedes editar manualmente
6. Editar el resultado final eligiendo qué cambios conservar
7. Click en **"Accept"** para marcar el conflicto como resuelto
8. Git → Commit → Mensaje: "Resueltos conflictos de fusión"
9. Git → Remote → Push

Ahora la PR se puede fusionar sin conflictos.

## Resumen de operaciones Git en NetBeans

### Operaciones principales utilizadas en el ejercicio:

| Operación | Ruta en NetBeans | Descripción |
|-----------|------------------|-------------|
| **Clonar repositorio** | Team → Git → Clone | Descargar el repositorio remoto a local |
| **Inicializar Git** | Versioning → Initialize Git Repository | Crear repositorio Git en proyecto existente |
| **Añadir remoto** | Git → Remote → Add | Conectar con repositorio de GitHub |
| **Crear rama** | Git → Branch/Tag → Create Branch | Crear nueva rama de desarrollo |
| **Cambiar de rama** | Git → Branch → Switch to Branch | Moverse entre ramas |
| **Ver cambios** | Git → Show Changes | Ver archivos modificados |
| **Commit** | Git → Commit | Guardar cambios en repositorio local |
| **Push to Upstream** | Git → Remote → Push to Upstream | Subir rama nueva y establecer seguimiento |
| **Push** | Git → Remote → Push | Subir cambios a rama ya existente |
| **Pull from Upstream** | Git → Remote → Pull from Upstream | Descargar cambios del remoto |
| **Resolver conflictos** | Clic derecho → Git → Resolve Conflicts | Abrir editor de conflictos |
| **Crear tag** | Git → Tag → Create Tag | Etiquetar versión |
| **Push Tags** | Git → Remote → Push Tags | Subir etiquetas al remoto |

### Comandos de terminal (solo referencia)

Si necesitas usar comandos Git desde terminal, aquí están los equivalentes:

```bash
# Ver rama actual
git branch

# Ver estado de archivos
git status

# Ver historial de commits
git log --oneline --graph --all

# Ver ramas remotas
git branch -r

# Cambiar de rama
git checkout nombre-rama

# Crear y cambiar a nueva rama
git checkout -b nombre-rama

# Ver diferencias
git diff
```

> **Nota**: En este ejercicio **todo se realiza desde NetBeans**. Los comandos de terminal son solo para referencia informativa.


## Buenas prácticas aplicadas

✅ **Cada desarrollador trabaja en su propia rama** - Evita conflictos
✅ **Nombres descriptivos de ramas** - `feature/funcionalidad`
✅ **Commits frecuentes con mensajes claros** - Facilita seguimiento
✅ **Pull Requests para fusionar** - Permite revisión
✅ **Revisión de código** - Mejora la calidad
✅ **Sincronización regular** - `git pull` frecuente
✅ **Rama main protegida** - Solo se fusiona mediante PR


## Preguntas de reflexión

1. ¿Por qué es importante que cada desarrollador trabaje en su propia rama?
2. ¿Qué ventajas tiene fusionar en GitHub en lugar de localmente?
3. ¿Qué pasaría si dos desarrolladores modifican la misma línea de código?
4. ¿Cuándo deberías hacer `git pull`?
5. ¿Por qué es importante revisar el código antes de fusionar?


## Entregables

1. **Capturas de pantalla:**
   - Pull Request creada
   - Código revisado y aprobado
   - Merge exitoso
   - Gráfico de ramas en GitHub: Ir a la pestaña **Insights** en el repositorio, luego seleccionar **Network** en el menú lateral izquierdo

2. **Repositorio GitHub:**
   - URL del repositorio
   - Historial de commits visible
   - Todas las ramas fusionadas

3. **Documento de reflexión:**
   - Dificultades encontradas
   - Cómo se resolvieron los conflictos (si los hubo)
   - Aprendizajes del trabajo colaborativo

---

## Ampliaciones

### Protección de rama main (Branch Protection Rules)

**Nota**: La protección de rama **NO está activada por defecto** en GitHub. Es una configuración que debe establecer el propietario del repositorio.

Para activar la protección de la rama main:
1. Ir a **Settings** → **Branches** en el repositorio de GitHub
2. En "Branch protection rules", click en **Add rule**
3. En "Branch name pattern" escribir: `main`
4. Activar las opciones recomendadas:
   - ✅ **Require a pull request before merging** - Obliga a usar PR, no se puede hacer push directo a main
   - ✅ **Require approvals** (mínimo 1) - Al menos un revisor debe aprobar antes de fusionar
   - ✅ **Dismiss stale pull request approvals when new commits are pushed** - Si hay nuevos cambios, se requiere nueva revisión
   - ✅ **Require conversation resolution before merging** - Resolver todos los comentarios antes de fusionar
5. Click en **Create** o **Save changes**

**Ventajas de proteger la rama main:**
- Evita commits accidentales directos a la rama principal
- Garantiza revisión de código antes de integrar
- Mejora la calidad del código
- Simula entornos profesionales de desarrollo

### Gestión de tareas con Issues y Projects

**Orden recomendado:**

**1. Crear Issues (Tareas individuales)**
- Los Issues se pueden crear independientemente, sin necesidad de un Project
- Cada Issue representa una tarea, bug o funcionalidad específica
- Cómo crear:
  1. Ir a la pestaña **Issues** en GitHub
  2. Click en **New issue**
  3. Título y descripción de la tarea
  4. Asignar a un desarrollador
  5. Añadir etiquetas (bug, enhancement, documentation, etc.)

**2. Crear Project Board (Organización visual)**
- El Project Board organiza y visualiza los Issues existentes
- Cómo crear:
  1. Ir a la pestaña **Projects** → **New project**
  2. Elegir template: "Board" (estilo Kanban) o "Table"
  3. Crear columnas típicas: "To Do", "In Progress", "Done"
  4. **Añadir Issues al Project**: Arrastrar los Issues creados a las columnas correspondientes

**Flujo de trabajo sugerido:**
1. Al inicio del sprint/semana: Crear Issues para todas las tareas
2. Crear un Project Board para visualizar el progreso
3. Añadir los Issues al Project
4. Mover los Issues entre columnas según avanza el trabajo
5. Cerrar Issues cuando se complete y fusione la PR correspondiente

**Ejemplo práctico:**
- Issue #1: "Añadir función de suma" → Asignado a Dev A
- Issue #2: "Añadir función de multiplicación" → Asignado a Dev B
- Issue #3: "Crear menú interactivo" → Asignado a Dev C
- Project Board "Sprint 1" con estos 3 issues organizados

> **Nota**: No es obligatorio tener un Project para usar Issues. Los Issues funcionan de forma independiente, pero el Project ayuda a organizar visualmente el trabajo del equipo.

### Otras ampliaciones

- Configurar GitHub Actions para tests automáticos
- Vincular Pull Requests con Issues usando palabras clave (fixes #1, closes #2)
- Añadir más funcionalidades en nuevas ramas

## Referencias

- [Documentación oficial de Git](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [NetBeans Git Support](https://netbeans.apache.org/kb/docs/ide/git.html)
- [Git Flow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
