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

---

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

**Opción A: Clonar el repositorio y añadir el proyecto**
```bash
# En terminal
git clone https://github.com/usuario/CalculadoraEquipo.git
# Mover los archivos del proyecto de NetBeans a la carpeta clonada
```

**Opción B: Inicializar Git en el proyecto existente**

Desde NetBeans:
1. Clic derecho en el proyecto → Versioning → Initialize Git Repository
2. Seleccionar la carpeta del proyecto
3. Añadir el remoto desde terminal o Git Bash:
   ```bash
   git remote add origin https://github.com/usuario/CalculadoraEquipo.git
   git branch -M main
   git pull origin main --allow-unrelated-histories
   ```

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
4. Commit and Push
5. Seleccionar la rama `main`
6. Push

### Paso 1.6: Invitar a los colaboradores

En GitHub:
1. Ir a Settings → Collaborators
2. Añadir los usuarios de GitHub de los Desarrolladores B y C
3. Los desarrolladores deben aceptar la invitación por email

---

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
3. Marcar "Switch to New Branch"
4. Create

**Verificar rama actual:**
- En la esquina inferior derecha de NetBeans se muestra la rama activa

### Paso 2.3: Publicar la rama en GitHub

Después de crear la rama local:
1. Clic derecho en el proyecto → Git → Remote → Push to Upstream
2. Esto creará la rama en GitHub automáticamente

---

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
3. Commit and Push
4. Push to: `origin/feature/suma-resta`

---

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
3. Commit and Push
4. Push to: `origin/feature/multiplicacion-division`

---

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
                    case 1:
                        System.out.println("Resultado: " + num1 + " + " + num2 + " = " + (num1 + num2));
                        break;
                    case 2:
                        System.out.println("Resultado: " + num1 + " - " + num2 + " = " + (num1 - num2));
                        break;
                    case 3:
                        System.out.println("Resultado: " + num1 + " * " + num2 + " = " + (num1 * num2));
                        break;
                    case 4:
                        if (num2 != 0) {
                            System.out.println("Resultado: " + num1 + " / " + num2 + " = " + (num1 / num2));
                        } else {
                            System.out.println("Error: No se puede dividir entre cero");
                        }
                        break;
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
3. Commit and Push
4. Push to: `origin/feature/menu`

---

## Fase 4: Integración en GitHub (Pull Requests)

### ¿Por qué fusionar en el repositorio remoto?

**Ventajas de fusionar en GitHub (remoto):**
- ✅ **Revisión de código**: Otros pueden revisar antes de integrar
- ✅ **Documentación**: Queda registro de quién revisó y aprobó
- ✅ **Detección de conflictos**: GitHub avisa antes de fusionar
- ✅ **Pruebas automatizadas**: Se pueden configurar tests antes del merge
- ✅ **Seguridad**: La rama principal está protegida
- ✅ **Trazabilidad**: Historial claro de cambios

### Paso 4.1: Crear Pull Requests (Cada desarrollador)

**En GitHub (navegador web):**

1. Ir al repositorio en GitHub
2. Aparecerá un mensaje: "Your recently pushed branches"
3. Click en **"Compare & pull request"** para tu rama
4. Rellenar la Pull Request:
   - **Title**: Descripción clara (ej: "Añadir clase Libro")
   - **Description**: Detalles de los cambios realizados
   - **Reviewers**: Asignar a otro miembro del equipo
   - **Assignees**: Asignarte a ti mismo
5. Click en **"Create pull request"**

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

### Paso 4.2: Revisión de código (Desarrollador asignado)

El revisor debe:
1. Ir a la pestaña **"Pull requests"**
2. Abrir la PR asignada
3. Revisar los cambios en **"Files changed"**
4. Añadir comentarios si hay sugerencias
5. Si todo está correcto: **"Review changes"** → **"Approve"**

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

**Después de cada fusión, todos deben actualizar:**

1. Cambiar a la rama main:
   - Git → Branch → Switch to Branch → `main`
2. Obtener cambios:
   - Git → Remote → Pull from Upstream
   - O: Clic derecho → Git → Pull

**En terminal (alternativa):**
```bash
git checkout main
git pull origin main
```

---

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

**Opción 2: Resolver localmente (conflictos complejos)**

En NetBeans:
```bash
# En terminal dentro del proyecto
git checkout feature/readme-C
git pull origin main
```

1. NetBeans mostrará los archivos en conflicto (icono rojo)
2. Clic derecho en archivo → Git → Resolve Conflicts
3. Editor de conflictos:
   - **Left**: Tu versión
   - **Right**: Versión de main
   - **Result**: Resultado final (editable)
4. Editar manualmente el resultado
5. Click en **"Accept"**
6. Git → Commit → "Resueltos conflictos de fusión"
7. Git → Push

Ahora la PR se puede fusionar sin conflictos.

---

## Fase 6: Integración final

### Paso 6.1: Sincronizar todos los cambios

**Todos los desarrolladores:**
```bash
git checkout main
git pull origin main
```

### Paso 6.2: Verificar el proyecto completo

1. Ejecutar el proyecto en NetBeans
2. Verificar que `Calculadora.java` contiene:
   - ✅ Menú interactivo
   - ✅ Operaciones de suma y resta
   - ✅ Operaciones de multiplicación y división
3. Probar todas las operaciones con diferentes números

### Paso 6.3: Crear tag de versión (Opcional)

**Desarrollador A:**
```bash
git tag -a v1.0 -m "Primera versión completa"
git push origin v1.0
```

---

## Resumen de comandos Git utilizados

### En NetBeans (interfaz gráfica):
- **Clone**: Team → Git → Clone
- **Create Branch**: Git → Branch/Tag → Create Branch
- **Commit**: Git → Commit
- **Push**: Git → Remote → Push to Upstream
- **Pull**: Git → Remote → Pull from Upstream
- **Switch Branch**: Git → Branch → Switch to Branch

### En terminal (complementarios):
```bash
# Ver rama actual
git branch

# Ver estado
git status

# Ver historial
git log --oneline --graph

# Ver ramas remotas
git branch -r

# Eliminar rama local
git branch -d nombre-rama
```

---

## Buenas prácticas aplicadas

✅ **Cada desarrollador trabaja en su propia rama** - Evita conflictos
✅ **Nombres descriptivos de ramas** - `feature/funcionalidad`
✅ **Commits frecuentes con mensajes claros** - Facilita seguimiento
✅ **Pull Requests para fusionar** - Permite revisión
✅ **Revisión de código** - Mejora la calidad
✅ **Sincronización regular** - `git pull` frecuente
✅ **Rama main protegida** - Solo se fusiona mediante PR

---

## Preguntas de reflexión

1. ¿Por qué es importante que cada desarrollador trabaje en su propia rama?
2. ¿Qué ventajas tiene fusionar en GitHub en lugar de localmente?
3. ¿Qué pasaría si dos desarrolladores modifican la misma línea de código?
4. ¿Cuándo deberías hacer `git pull`?
5. ¿Por qué es importante revisar el código antes de fusionar?

---

## Entregables

1. **Capturas de pantalla:**
   - Pull Request creada
   - Código revisado y aprobado
   - Merge exitoso
   - Gráfico de ramas en GitHub (Insights → Network)

2. **Repositorio GitHub:**
   - URL del repositorio
   - Historial de commits visible
   - Todas las ramas fusionadas

3. **Documento de reflexión:**
   - Dificultades encontradas
   - Cómo se resolvieron los conflictos (si los hubo)
   - Aprendizajes del trabajo colaborativo

---

## Ampliaciones opcionales

- Configurar GitHub Actions para tests automáticos
- Implementar protección de rama main (require reviews)
- Usar Issues para planificar tareas
- Crear un Project Board para seguimiento
- Añadir más funcionalidades en nuevas ramas

---

## Referencias

- [Documentación oficial de Git](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [NetBeans Git Support](https://netbeans.apache.org/kb/docs/ide/git.html)
- [Git Flow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
