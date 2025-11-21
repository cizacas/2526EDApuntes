#### ED - 1ºCFGS DAM <img src="img/logo.jpg" style="float: right; width: 180px; height: 46px">
<div style="text-align: center;"><strong>Unidad 3 - Actividad 3</strong></div>

---

## Fase 6: Documentación del proyecto

Una vez que todas las funcionalidades están integradas, es fundamental documentar el proyecto. La documentación es tan importante como el código y debe hacerse de forma colaborativa.

### Objetivos de esta fase:
- Crear documentación del proyecto con **Markdown** (README.md)
- Documentar el código fuente con **Javadoc**
- Generar la documentación HTML automáticamente

### Paso 6.1: Documentación con Markdown - README.md

**Desarrollador asignado: Desarrollador C**

El Desarrollador C creará un README.md profesional para el proyecto. Consulta el **[Manual de Markdown](Markdown.md)** para ayudarte.

**Crear rama de documentación:**
1. Asegurarse de estar en `main` actualizada:
   - Git → Branch → Switch to Branch → `main`
   - Git → Remote → Pull from Upstream
2. Crear nueva rama desde NetBeans:
   - Git → Branch/Tag → Create Branch
   - Nombre: `docs/readme`
   - Switch to New Branch: ✅

**Crear el archivo README.md:**

En la raíz del proyecto (mismo nivel que `src/`), crear el archivo `README.md` con el siguiente contenido mínimo:

```markdown
# Calculadora Básica en Java

Proyecto colaborativo desarrollado por el equipo [Nombre del equipo] como ejercicio de trabajo en equipo con Git y GitHub.

## Descripción

Aplicación de consola que implementa una calculadora con operaciones matemáticas básicas:
- ✅ Suma
- ✅ Resta
- ✅ Multiplicación
- ✅ División
- ✅ Menú interactivo

## Tecnologías utilizadas

- **Lenguaje**: Java
- **IDE**: NetBeans
- **Control de versiones**: Git
- **Plataforma**: GitHub

## Instalación y ejecución

### Requisitos previos
- Java JDK 8 o superior
- NetBeans IDE (o cualquier IDE compatible con Java)

### Pasos de instalación
1. Clonar el repositorio:
   ```bash
   git clone https://github.com/usuario/CalculadoraEquipo.git
   ```
2. Abrir el proyecto en NetBeans
3. Ejecutar la clase principal `Calculadora.java`

## Uso

Al ejecutar el programa, se mostrará un menú con las siguientes opciones:

```
=== Calculadora Básica ===
1. Sumar
2. Restar
3. Multiplicar
4. Dividir
0. Salir
Seleccione una opción:
```

Introduce el número de la operación deseada, luego ingresa los dos números y obtendrás el resultado.

## Estructura del proyecto

```
CalculadoraEquipo/
├── src/
│   └── calculadora/
│       └── Calculadora.java
├── README.md
└── .gitignore
```

## Equipo de desarrollo

- **Desarrollador A**: Funciones de suma y resta
- **Desarrollador B**: Funciones de multiplicación y división  
- **Desarrollador C**: Menú interactivo y documentación

## Versionado

Utilizamos Git para el control de versiones. Puedes ver todas las versiones disponibles en los [tags de este repositorio](https://github.com/usuario/CalculadoraEquipo/tags).

**Versión actual**: 1.0

## Licencia

Este proyecto es un ejercicio educativo del módulo de Entornos de Desarrollo.

## Contacto

Para dudas o sugerencias, contactar a través de GitHub Issues.

> **Nota**: Personaliza el README.md con los nombres reales de tu equipo y la URL correcta de vuestro repositorio.

**Commit y Push:**
1. Git → Commit
2. Mensaje: "Añadida documentación del proyecto en README.md"
3. Commit y Push to Upstream

**Crear Pull Request en GitHub:**
1. Ir a GitHub → Compare & pull request
2. Title: "Documentación: Añadir README.md del proyecto"
3. Reviewers: Desarrollador A (Líder)
4. Create pull request

**Revisión y fusión:**
- Desarrollador A revisa y aprueba
- Desarrollador A fusiona la PR en `main`
- Todos actualizan su repositorio local (Pull from Upstream)

### Paso 6.2: Documentación con Javadoc

**Desarrolladores asignados: Desarrollador A y Desarrollador B**

Ahora documentar el código fuente utilizando comentarios Javadoc. Consulta el **[Manual de Javadoc](Javadoc.md)** para ayudarte.

**Desarrollador A: Documentar clase y métodos de suma/resta**

1. Crear nueva rama desde `main` actualizada:
   - Nombre: `docs/javadoc-suma-resta`
2. Modificar `Calculadora.java` añadiendo comentarios Javadoc:

```java
package calculadora;

import java.util.Scanner;

/**
 * Clase principal de la calculadora básica.
 * Proporciona operaciones matemáticas elementales: suma, resta, 
 * multiplicación y división.
 * 
 * @author Desarrollador A, Desarrollador B, Desarrollador C
 * @version 1.0
 * @since 2024-11-21
 */
public class Calculadora {
    
    /**
     * Método principal que ejecuta el menú interactivo de la calculadora.
     * Permite al usuario seleccionar operaciones y realizar cálculos.
     * 
     * @param args argumentos de línea de comandos (no utilizados)
     */
    public static void main(String[] args) {
        // ... código del main existente ...
    }
    
    /**
     * Suma dos números decimales.
     * 
     * @param num1 primer número a sumar
     * @param num2 segundo número a sumar
     * @return la suma de num1 y num2
     */
    public static double sumar(double num1, double num2) {
        return num1 + num2;
    }
    
    /**
     * Resta dos números decimales.
     * 
     * @param num1 el minuendo (número al que se le resta)
     * @param num2 el sustraendo (número que se resta)
     * @return la diferencia entre num1 y num2 (num1 - num2)
     */
    public static double restar(double num1, double num2) {
        return num1 - num2;
    }
    
    // ... resto del código sin cambios ...
}
```

3. Commit y Push: "Añadida documentación Javadoc para suma y resta"
4. Crear PR en GitHub
5. Desarrollador A revisa y fusiona

**Desarrollador B: Documentar métodos de multiplicación/división**

1. Actualizar `main` local (Pull from Upstream)
2. Crear nueva rama desde `main`:
   - Nombre: `docs/javadoc-mult-div`
3. Modificar `Calculadora.java` añadiendo Javadoc a sus métodos:

```java
    /**
     * Multiplica dos números decimales.
     * 
     * @param num1 primer factor de la multiplicación
     * @param num2 segundo factor de la multiplicación
     * @return el producto de num1 por num2
     */
    public static double multiplicar(double num1, double num2) {
        return num1 * num2;
    }
    
    /**
     * Divide dos números decimales.
     * Si el divisor es cero, muestra un mensaje de error y retorna 0.
     * 
     * @param num1 el dividendo (número a dividir)
     * @param num2 el divisor (número por el que se divide)
     * @return el cociente de num1 entre num2, o 0 si num2 es cero
     */
    public static double dividir(double num1, double num2) {
        if (num2 != 0) {
            return num1 / num2;
        } else {
            System.out.println("Error: No se puede dividir entre cero");
            return 0;
        }
    }
```

4. Commit y Push: "Añadida documentación Javadoc para multiplicación y división"
5. Crear PR en GitHub
6. Desarrollador A revisa y fusiona
7. Todos actualizan su repositorio local

### Paso 6.3: Generar documentación HTML con Javadoc

**Desarrollador asignado: Desarrollador A**

Una vez que todo el código está documentado con Javadoc, genera la documentación HTML.

**En NetBeans:**
1. Asegurarse de estar en rama `main` actualizada
2. Clic derecho en el proyecto → **Generate Javadoc**
3. NetBeans generará la documentación HTML

**Ubicación de la documentación generada:**
- **Proyectos Ant**: `dist/javadoc/index.html`
- **Proyectos Maven**: `target/reports/apidocs/index.html`

**Visualizar la documentación:**
1. Navegar hasta la carpeta correspondiente
2. Abrir `index.html` en el navegador
3. Verificar que aparecen:
   - Descripción de la clase `Calculadora`
   - Todos los métodos documentados con sus parámetros y retornos
   - Los comentarios Javadoc convertidos a HTML profesional

**Compartir resultados con el equipo:**
- Hacer capturas de pantalla de la documentación HTML generada
- Compartir en el grupo para verificar que todo está correcto

> **Nota importante**: Los archivos HTML generados NO se suben al repositorio (están en `.gitignore`). Cada desarrollador puede generar la documentación localmente cuando la necesite ejecutando "Generate Javadoc" en NetBeans.

### Resultado de esta fase

Al finalizar la Fase 6, el proyecto tendrá:
- ✅ **README.md** completo con toda la información del proyecto (Markdown)
- ✅ **Código fuente documentado** con comentarios Javadoc profesionales
- ✅ **Documentación HTML** generada automáticamente
- ✅ **Historial de Git** mostrando las ramas de documentación fusionadas

**Captura requerida para entrega:**
- Captura de la documentación HTML generada mostrando la clase `Calculadora` con todos sus métodos documentados

## Fase 7: Integración final

### Paso 7.1: Sincronizar todos los cambios

**Todos los desarrolladores deben actualizar su repositorio local desde NetBeans:**

1. Cambiar a la rama main:
   - Git → Branch → Switch to Branch → `main`
2. Traer todos los cambios del repositorio remoto:
   - Git → Remote → Pull from Upstream
   - Esto descargará todas las fusiones realizadas

### Paso 7.2: Verificar el proyecto completo

1. Ejecutar el proyecto en NetBeans (F6 o Run)
2. Verificar que `Calculadora.java` contiene:
   - ✅ Menú interactivo
   - ✅ Operaciones de suma y resta
   - ✅ Operaciones de multiplicación y división
3. Probar todas las operaciones con diferentes números

### Paso 7.3: Crear tag de versión (Opcional)

**Desarrollador A desde NetBeans:**

1. Clic derecho en el proyecto → Git → Tag → Create Tag
2. Tag Name: `v1.0`
3. Tag Message: `Primera versión completa`
4. Click en **Create Tag**
5. Publicar el tag en GitHub:
   - Git → Remote → Push Tags
   - Seleccionar el tag `v1.0`
   - Push

---

## Entregables

1. **Documentación:**
   - README.md completo y visible en GitHub
   - Captura de la documentación Javadoc HTML generada
