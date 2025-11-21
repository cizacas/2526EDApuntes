# Manual básico de Javadoc

## ¿Qué es Javadoc?

**Javadoc** es una herramienta estándar de Java que genera documentación HTML automáticamente a partir de comentarios especiales en el código fuente. Está integrada en NetBeans y permite crear documentación profesional de tus clases, métodos y variables.

> **⚠️ MUY IMPORTANTE**: 
> 
> **Javadoc NO crea la documentación, solo la CONVIERTE a HTML**.
> 
> - **Tú escribes** los comentarios `/**  */` en tu código
> - **Javadoc lee** esos comentarios y genera páginas HTML bonitas
> - **Si no escribes comentarios, Javadoc generará HTML vacío o solo con la estructura básica**
>
> **Analogía**: Javadoc es como una impresora. Si le das un documento en blanco, imprimirá una hoja en blanco. Si le das un documento bien escrito, imprimirá algo útil.

### Ventajas de usar Javadoc:
- ✅ **Documentación automática**: Genera HTML navegable sin esfuerzo adicional
- ✅ **Estándar de la industria**: Formato reconocido en todo el mundo Java
- ✅ **Integración IDE**: NetBeans genera automáticamente plantillas
- ✅ **Ayuda al equipo**: Otros programadores entienden tu código fácilmente
- ✅ **Autocompletado**: Los IDEs muestran la documentación mientras escribes código

## Tipos de comentarios en Java

### 1. Comentarios de una línea
```java
// Este es un comentario de una línea
int edad = 25; // Comentario al final de una línea
```

### 2. Comentarios de múltiples líneas
```java
/*
 * Este es un comentario
 * de múltiples líneas
 */
```

### 3. Comentarios Javadoc
```java
/**
 * Este es un comentario Javadoc
 * que genera documentación automática
 */
```

> **Importante**: Los comentarios Javadoc usan `/**` (dos asteriscos) al inicio.

## Estructura básica de Javadoc

### Documentar una clase

```java
/**
 * Clase que representa un estudiante del ciclo de DAM.
 * Almacena la información básica del alumno.
 * 
 * @author Nombre del Autor
 * @version 1.0
 * @since 2024-11-21
 */
public class Estudiante {
    // Contenido de la clase
}
```

### Documentar atributos

```java
/**
 * Nombre completo del estudiante
 */
private String nombre;

/**
 * Edad del estudiante en años
 */
private int edad;

/**
 * Nota media del expediente académico (0.0 - 10.0)
 */
private double notaMedia;
```

### Documentar métodos

```java
/**
 * Calcula la nota final del estudiante sumando teoría y práctica.
 * 
 * @param notaTeoria Nota del examen teórico (0-10)
 * @param notaPractica Nota del examen práctico (0-10)
 * @return La nota final calculada como media de ambas notas
 * @throws IllegalArgumentException si alguna nota es negativa o mayor que 10
 */
public double calcularNotaFinal(double notaTeoria, double notaPractica) {
    if (notaTeoria < 0 || notaTeoria > 10 || notaPractica < 0 || notaPractica > 10) {
        throw new IllegalArgumentException("Las notas deben estar entre 0 y 10");
    }
    return (notaTeoria + notaPractica) / 2.0;
}
```

### Documentar constructores

```java
/**
 * Constructor que crea un estudiante con todos sus datos.
 * 
 * @param nombre Nombre completo del estudiante
 * @param edad Edad del estudiante (debe ser mayor que 0)
 * @param notaMedia Nota media inicial del expediente
 */
public Estudiante(String nombre, int edad, double notaMedia) {
    this.nombre = nombre;
    this.edad = edad;
    this.notaMedia = notaMedia;
}

/**
 * Constructor por defecto que crea un estudiante sin datos iniciales.
 * Los valores se establecen a valores por defecto.
 */
public Estudiante() {
    this.nombre = "";
    this.edad = 0;
    this.notaMedia = 0.0;
}
```

## Etiquetas principales de Javadoc

| Etiqueta | Uso | Descripción |
|----------|-----|-------------|
| `@author` | Clases | Nombre del autor del código |
| `@version` | Clases | Versión de la clase o proyecto |
| `@since` | Clases/Métodos | Desde qué versión existe |
| `@param` | Métodos | Describe un parámetro del método |
| `@return` | Métodos | Describe el valor que devuelve |
| `@throws` | Métodos | Describe las excepciones que puede lanzar |
| `@deprecated` | Cualquiera | Indica que está obsoleto |
| `@see` | Cualquiera | Referencia a otra clase o método |

## Generar comentarios Javadoc en NetBeans

### Método rápido (autocompletado):

1. Sitúa el cursor **justo encima** de la clase, método o constructor
2. Escribe `/**` y pulsa **Enter**
3. NetBeans genera automáticamente la plantilla con todas las etiquetas necesarias

**Ejemplo:**

```java
// Escribes esto justo encima del método:
/**

// Al pulsar Enter, NetBeans genera automáticamente:
/**
 * 
 * @param notaTeoria
 * @param notaPractica
 * @return 
 */
public double calcularNotaFinal(double notaTeoria, double notaPractica) {
    // ...
}
```

Luego solo completas las descripciones.

## Ejemplo completo de clase documentada

```java
package dam.entornos;

/**
 * Clase que representa un libro en una biblioteca.
 * Permite gestionar la información básica de un libro y 
 * controlar su disponibilidad para préstamos.
 * 
 * @author María García
 * @version 1.0
 * @since 2024-11-21
 */
public class Libro {
    
    /**
     * Código ISBN único del libro
     */
    private String isbn;
    
    /**
     * Título del libro
     */
    private String titulo;
    
    /**
     * Autor o autores del libro
     */
    private String autor;
    
    /**
     * Indica si el libro está disponible para préstamo
     */
    private boolean disponible;
    
    /**
     * Constructor que crea un libro con todos sus datos.
     * Por defecto el libro se marca como disponible.
     * 
     * @param isbn Código ISBN del libro (debe ser válido)
     * @param titulo Título del libro
     * @param autor Nombre del autor
     */
    public Libro(String isbn, String titulo, String autor) {
        this.isbn = isbn;
        this.titulo = titulo;
        this.autor = autor;
        this.disponible = true;
    }
    
    /**
     * Obtiene el código ISBN del libro.
     * 
     * @return El código ISBN
     */
    public String getIsbn() {
        return isbn;
    }
    
    /**
     * Obtiene el título del libro.
     * 
     * @return El título del libro
     */
    public String getTitulo() {
        return titulo;
    }
    
    /**
     * Comprueba si el libro está disponible para préstamo.
     * 
     * @return true si está disponible, false en caso contrario
     */
    public boolean isDisponible() {
        return disponible;
    }
    
    /**
     * Marca el libro como prestado si está disponible.
     * 
     * @return true si se pudo prestar, false si ya estaba prestado
     */
    public boolean prestar() {
        if (disponible) {
            disponible = false;
            return true;
        }
        return false;
    }
    
    /**
     * Devuelve el libro a la biblioteca marcándolo como disponible.
     */
    public void devolver() {
        disponible = true;
    }
    
    /**
     * Genera una representación en texto del libro.
     * 
     * @return String con el formato "Título - Autor (ISBN)"
     */
    @Override
    public String toString() {
        return titulo + " - " + autor + " (" + isbn + ")";
    }
}
```

## Generar documentación HTML en NetBeans

### Proyecto Maven vs Proyecto Java estándar

NetBeans genera el Javadoc en diferentes ubicaciones según el tipo de proyecto:

- **Proyecto Java estándar (Ant)**: `dist/javadoc/`
- **Proyecto Maven**: `target/reports/apidocs/`

### Opción 1: Generar Javadoc del proyecto completo

**Para proyectos Java estándar (Ant):**
1. Clic derecho en el proyecto → **Generate Javadoc**
2. NetBeans genera la documentación HTML en la carpeta `dist/javadoc/`
3. Se abre automáticamente en el navegador

**Para proyectos Maven:**
1. Clic derecho en el proyecto → **Generate Javadoc**
2. O desde el menú: **Run** → **Generate Javadoc**
3. Maven ejecuta el plugin javadoc
4. La documentación se genera en: `target/reports/apidocs/`
5. **Importante**: Debes abrir manualmente el archivo `index.html` que está en esa carpeta

**Si no se abre automáticamente en Maven:**
1. Ve a la carpeta del proyecto en el explorador de archivos
2. Navega a: `target/reports/apidocs/`
3. Abre el archivo `index.html` con tu navegador web

### Opción 2: Ver la documentación generada en NetBeans

**Desde el explorador de archivos de NetBeans:**
1. En la pestaña **Files** (no Projects), expande tu proyecto
2. Busca la carpeta:
   - Ant: `dist/javadoc/`
   - Maven: `target/reports/apidocs/`
3. Clic derecho en `index.html` → **View**

### Opción 3: Configurar Maven para abrir automáticamente

Si quieres que Maven abra el navegador automáticamente, añade esta configuración al `pom.xml`:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-javadoc-plugin</artifactId>
            <version>3.12.0</version>
            <configuration>
                <show>private</show>
                <nohelp>true</nohelp>
            </configuration>
        </plugin>
    </plugins>
</build>
```

Luego genera el Javadoc con:
- Clic derecho en proyecto → **Build with Dependencies**

### Opción 4: Ver documentación de un método (cualquier tipo de proyecto)

1. Sitúa el cursor sobre un método documentado
2. Pulsa **Ctrl + Shift + Space** (Windows/Linux) o **Cmd + Shift + Space** (Mac)
3. Aparece un popup con la documentación Javadoc

### Solución de problemas en Maven

> **⚠️ IMPORTANTE - Diferencia entre plugin de NetBeans y plugin de Maven:**
> 
> - **Plugin de NetBeans**: Es la funcionalidad que viene integrada en NetBeans IDE para trabajar con Javadoc (autocompletado `/**`, sintaxis, etc.). **Ya viene instalado** en NetBeans, no necesitas instalarlo.
> 
> - **Plugin de Maven (maven-javadoc-plugin)**: Es una herramienta de Maven que se configura en el `pom.xml` para generar la documentación HTML. **No es un plugin de NetBeans**, es parte de tu proyecto Maven.
>
> **En resumen**: NetBeans ya sabe trabajar con Javadoc. Lo que puede faltar es la configuración en el `pom.xml` para que Maven genere el HTML.

**Si no se genera nada:**

1. **Verifica que tienes comentarios Javadoc**: Maven solo genera documentación si existen comentarios `/**  */` en tu código

2. **Asegúrate de que el código compila**: Ejecuta **Clean and Build** primero

3. **Añade el plugin de Javadoc al `pom.xml`** (si no lo tiene):
   
   Abre tu archivo `pom.xml` y añade esta configuración dentro de `<project>`:
   
   ```xml
   <build>
       <plugins>
           <plugin>
               <groupId>org.apache.maven.plugins</groupId>
               <artifactId>maven-javadoc-plugin</artifactId>
               <version>3.12.0</version>
               <configuration>
                   <show>private</show>
                   <nohelp>true</nohelp>
                   <encoding>UTF-8</encoding>
                   <charset>UTF-8</charset>
                   <docencoding>UTF-8</docencoding>
               </configuration>
           </plugin>
       </plugins>
   </build>
   ```
   
   **Nota**: Esta configuración la añades tú manualmente al `pom.xml`, no se instala desde ningún menú de NetBeans.

4. **Revisa las propiedades del proyecto**: Añade esto al `pom.xml` si no lo tienes:
   ```xml
   <properties>
       <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
       <maven.compiler.release>21</maven.compiler.release>
   </properties>
   ```

5. **Ejecuta desde NetBeans situada en el proyecto Generate Javadoc** 

6. **Revisa la salida**: Si hay errores en los comentarios Javadoc o problemas de configuración, Maven los mostrará

**Verificar que se generó correctamente:**
- Comprueba que existe la carpeta `target/reports/apidocs/` en la raíz de tu proyecto
- Dentro debe haber archivos HTML (index.html, overview-tree.html, etc.)
- Abre `index.html` directamente con el navegador

### Entender los warnings (advertencias) de Javadoc

Cuando generas Javadoc, es **normal** que aparezcan warnings. Estos son **avisos, no errores**, y el HTML se genera igualmente. Los warnings más comunes son:

#### Warning: "no main description"
```
warning: no main description
* @author cic
^
```
**Significado**: Tienes `@author` pero falta la descripción principal de la clase.

**Solución**: Añade texto antes de las etiquetas:
```java
/**
 * Clase principal del programa.
 * Realiza cálculos básicos de notas.
 * 
 * @author cic
 * @version 1.0
 */
public class Ejemplo1 {
```

#### Warning: "use of default constructor, which does not provide a comment"
```
warning: use of default constructor, which does not provide a comment
public class Ejemplo1 {
```
**Significado**: La clase tiene un constructor por defecto (implícito) sin documentar.

**Solución**: Si no necesitas documentar el constructor, puedes ignorar este warning. O crea un constructor explícito documentado:
```java
/**
 * Constructor por defecto.
 */
public Ejemplo1() {
}
```

#### Warning: "no comment"
```
warning: no comment
public static void main(String[] args) {
```
**Significado**: El método no tiene comentario Javadoc.

**Solución**: Añade documentación:
```java
/**
 * Método principal de la aplicación.
 * 
 * @param args Argumentos de línea de comandos (no se utilizan)
 */
public static void main(String[] args) {
    // código
}
```

#### Ejemplo completo corregido

**Antes (con warnings):**
```java
/**
 * @author cic
 */
public class Ejemplo1 {
    
    public static void main(String[] args) {
        System.out.println("Nota final: " + calcularNotaFinal(7.5, 8.0));
    }
    
    public static double calcularNotaFinal(double notaTeoria, double notaPractica) {
        return (notaTeoria + notaPractica) / 2.0;
    }
}
```

**Después (sin warnings):**
```java
/**
 * Clase principal que calcula la nota final de un estudiante.
 * Permite calcular la media entre la nota de teoría y práctica.
 * 
 * @author cic
 * @version 1.0
 */
public class Ejemplo1 {
    
    /**
     * Método principal de la aplicación.
     * Muestra un ejemplo de cálculo de nota final.
     * 
     * @param args Argumentos de línea de comandos (no utilizados)
     */
    public static void main(String[] args) {
        System.out.println("Nota final: " + calcularNotaFinal(7.5, 8.0));
    }
    
    /**
     * Calcula la nota final como media aritmética de teoría y práctica.
     * 
     * @param notaTeoria Nota del examen teórico (0-10)
     * @param notaPractica Nota del examen práctico (0-10)
     * @return La nota final (media de ambas notas)
     */
    public static double calcularNotaFinal(double notaTeoria, double notaPractica) {
        return (notaTeoria + notaPractica) / 2.0;
    }
}
```

**Resultado**: 0 warnings y documentación HTML completa generada en `target/reports/apidocs/index.html`

> **Nota importante**: Los warnings NO impiden que se genere el HTML. Puedes abrir `target/reports/apidocs/index.html` incluso con warnings, pero es mejor corregirlos para tener documentación completa y profesional.

## Buenas prácticas de documentación

### ✅ SÍ hacer:

- **Documentar todo lo público**: Clases, métodos y constructores públicos siempre
- **Ser claro y conciso**: Descripciones breves pero completas
- **Usar verbos en tercera persona**: "Calcula", "Obtiene", "Devuelve"
- **Documentar parámetros**: Explicar qué representa cada parámetro
- **Documentar excepciones**: Indicar cuándo se lanzan
- **Mantener actualizado**: Actualizar la documentación cuando cambies el código

### ❌ NO hacer:

- **No documentar lo obvio**: Si un getter solo devuelve un valor, no hace falta mucho detalle
- **No repetir el código**: La documentación debe añadir valor, no repetir
- **No usar comentarios Javadoc para TODOs**: Usa `// TODO:` para tareas pendientes
- **No dejar plantillas vacías**: Si generas Javadoc automático, complétalo

## Ejemplos de documentación según el contexto

### Método simple (getter)
```java
/**
 * Obtiene el nombre del estudiante.
 * 
 * @return El nombre del estudiante
 */
public String getNombre() {
    return nombre;
}
```

### Método con lógica compleja
```java
/**
 * Calcula el factorial de un número usando recursividad.
 * El factorial de n (n!) es el producto de todos los números
 * positivos menores o iguales a n.
 * 
 * @param n El número del que calcular el factorial (debe ser >= 0)
 * @return El factorial de n
 * @throws IllegalArgumentException si n es negativo
 */
public long factorial(int n) {
    if (n < 0) {
        throw new IllegalArgumentException("El número no puede ser negativo");
    }
    if (n == 0 || n == 1) {
        return 1;
    }
    return n * factorial(n - 1);
}
```

### Método con múltiples parámetros
```java
/**
 * Busca un estudiante en la base de datos por nombre y apellido.
 * La búsqueda no distingue entre mayúsculas y minúsculas.
 * 
 * @param nombre Nombre del estudiante a buscar
 * @param apellido Apellido del estudiante a buscar
 * @param cursoBusqueda Curso en el que buscar (puede ser null para buscar en todos)
 * @return El estudiante encontrado o null si no existe
 * @see Estudiante
 */
public Estudiante buscarEstudiante(String nombre, String apellido, String cursoBusqueda) {
    // implementación
}
```

## Recursos adicionales

- [Documentación oficial de Javadoc](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/javadoc.html)
- [Guía de Oracle sobre cómo escribir Javadoc](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html)
- [Tutorial de Javadoc en NetBeans](https://netbeans.apache.org/tutorial/main/kb/docs/java/javadoc-learn/)

## Resumen rápido

1. **Usa `/**` + Enter** encima de clases, métodos y constructores
2. **Completa las descripciones** generadas automáticamente
3. **Documenta parámetros** con `@param`
4. **Documenta retornos** con `@return`
5. **Documenta excepciones** con `@throws`
6. **Genera HTML** con clic derecho → Generate Javadoc
7. **Mantén actualizada** la documentación cuando cambies el código
