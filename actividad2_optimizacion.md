#### ED - 1ºCFGS DAM <img src="img/logo.jpg" style="float: right; width: 180px; height: 46px">
<div style="text-align: center;"><strong>Unidad 3 - Actividad 2- Optimización</strong></div>

---


## Actividad 2: Refactorización y Optimización de Código Java

### Objetivo
Aplicar técnicas básicas de refactorización en código Java sencillo, mejorando la legibilidad, mantenibilidad y eficiencia del código. Se trabajará con clases simples que utilicen estructuras de control y arrays.


### Ejercicio 1:

A continuación se presenta una clase Java que gestiona las notas de un grupo de estudiantes. El código contiene varios aspectos que pueden mejorarse mediante refactorización. Analiza el código, identifica los problemas y realiza las modificaciones necesarias para optimizarlo y mejorar su calidad.

```java
public class NotasEstudiantes {
    String[] nombres = {"Ana", "Luis", "Marta", "Juan", "Sofía"};
    int[] notas = {7, 5, 9, 4, 6};

    public void mostrarNotas() {
        for (int i = 0; i < nombres.length; i++) {
            System.out.println(nombres[i] + ": " + notas[i]);
        }
    }

    public void aprobarEstudiantes() {
        for (int i = 0; i < notas.length; i++) {
            if (notas[i] >= 5) {
                System.out.println(nombres[i] + " ha aprobado");
            } else {
                System.out.println(nombres[i] + " ha suspendido");
            }
        }
    }

    public void notaMedia() {
        int suma = 0;
        for (int i = 0; i < notas.length; i++) {
            suma = suma + notas[i];
        }
        double media = suma / nombres.length;
        System.out.println("Nota media: " + media);
    }
}
```


### Ejercicio 2
A continuación se presenta otra clase Java que gestiona los precios de productos en una tienda. El código también contiene aspectos mejorables mediante refactorización. Analiza el código, identifica los problemas y realiza las modificaciones necesarias para optimizarlo y mejorar su calidad.

```java
public class PreciosTienda {
    String[] productos = {"Pan", "Leche", "Huevos", "Queso", "Manzanas"};
    double[] precios = {1.2, 0.95, 2.5, 3.8, 1.0};

    public void mostrarPrecios() {
        for (int i = 0; i < productos.length; i++) {
            System.out.println(productos[i] + ": " + precios[i] + " euros");
        }
    }

    public void precioMaximo() {
        double max = precios[0];
        int pos = 0;
        for (int i = 1; i < precios.length; i++) {
            if (precios[i] > max) {
                max = precios[i];
                pos = i;
            }
        }
        System.out.println("El producto más caro es " + productos[pos] + " con " + max + " euros");
    }

    public void productosBaratos(double limite) {
        for (int i = 0; i < precios.length; i++) {
            if (precios[i] < limite) {
                System.out.println(productos[i] + " es barato");
            }
        }
    }
}
```

### Tareas

1. **Analiza el código proporcionado y localiza los aspectos que pueden mejorarse mediante refactorización.**
2. **Refactoriza el código aplicando buenas prácticas de programación:**
   - Mejora la legibilidad y la organización del código.
   - Reduce la duplicidad y favorece la reutilización.
   - Utiliza nombres de variables y métodos más descriptivos si es necesario.
   - Aplica el principio de responsabilidad única en los métodos.
   - Corrige posibles errores o malas prácticas detectadas.
3. **Incluye comentarios en el código refactorizado explicando los cambios realizados.**
4. **Entrega:**
   - El código refactorizado en un archivo `.java`.
   - Un breve informe (puede ser en comentarios o en un documento aparte) justificando las mejoras aplicadas.

### Evaluación
Se valorará la correcta identificación de los problemas, la calidad de la refactorización, la claridad de los comentarios y la justificación de las mejoras aplicadas.
