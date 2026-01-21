#### ED - 1ºCFGS DAM <img src="img/logo.jpg" style="float: right; width: 180px; height: 46px">
<div style="text-align: center;"><strong>Unidad 3 - Actividad 1- Optimización</strong></div>

---


## Actividad 1: Refactorización y Optimización de Código Java

### Objetivo
Aplicar técnicas básicas de refactorización en código Java sencillo, mejorando la legibilidad, mantenibilidad y eficiencia del código. Se trabajará con clases simples que utilicen estructuras de control y arrays.

A continuación, se van a mostrar unos fragmentos de código. Para cada uno de ellos debes señalar que patrón desaconsejable identificas y explicar cómo lo solucionarías.

### Clase que calcula la factua de la electricidad:

```java
public class CalculaFacturaElectricidad {
public static void main(String args[]) {
long x;
Scanner teclado = new Scanner(System.in);
System.out.println("Introduzca la potencia consumida");
x = teclado.nextLong();
double y = 0;
if (x < 100) {
y = x * 1.20;
} else if (x < 300) {
y = 100 * 1.20 + (x - 100) * 2;
} else if (x > 300) {
y = 100 * 1.20 + 200 * 2 + (x - 300) * 3;
}
System.out.println("Debes pagar: " + y);
}
}
```

### Método para calcular el area

```java
public double Area(double radio) {
double area;
area = 3.1416 * Math.pow(radio,2);
return area;
}
```

### Método que calcula lo facturado

```java
public double calculaFacturado(double subtotal) {
double descuentoTotal = 0;
double totalFactura = 0;
double porcentajeDescuento;
if (subtotal >= 500) {
porcentajeDescuento = .25;
} else if (subtotal >= 200) {
porcentajeDescuento = .2;
} else if (subtotal >= 100) {
porcentajeDescuento = .1;
} else {
porcentajeDescuento = 0.0;
}
descuentoTotal = subtotal * porcentajeDescuento;
totalFactura = subtotal - descuentoTotal;
return totalFactura;
}
```
### Clase que calcula el area de las figuras

```java
public class CalculaAreaFiguras {
public static void main(String[] args) {
int opcion;
double area;
double lado;
double lado_rect1;
double lado_rect2;
double radio;
Scanner teclado = new Scanner(System.in);
System.out.println("1.- Calcular área cuadrado\n"
+ "2.- Calcular área rectángulo\n"
+ "3.- Calcular área círculo\n");
System.out.println(" Elige la opcion: ");
opcion = teclado.nextInt();
switch (opcion) {
case 1:
System.out.println("Introduzca el lado del cuadrado:");
lado = teclado.nextDouble();
area = lado * lado;
System.out.println("El area es: " + area);
break;
case 2:
System.out.println("Introduzca el primer lado del rectángulo:");
lado_rect1 = teclado.nextDouble();
System.out.println("Introduzca el segundo lado del rectángulo:");
lado_rect2 = teclado.nextDouble();
area = lado_rect1 * lado_rect2;
System.out.println("El area es: " + area);
break;
case 3:
System.out.println("Introduzca el radio del circulo:");
radio = teclado.nextDouble();
area = Math.PI * radio * radio;
System.out.println("El area es: " + area);
break;
}
System.out.println("Fin del programa");
}}
```

### Tareas

1. **Tabulación del código**, no es en sí una refactorización pero es una forma de que el código sea más claro y legible.
2. **Analiza el código proporcionado y localiza los aspectos que pueden mejorarse mediante refactorización.**
3. **Refactoriza el código aplicando buenas prácticas de programación:**
   - Mejora la legibilidad y la organización del código.
   - Reduce la duplicidad y favorece la reutilización.
   - Utiliza nombres de variables y métodos más descriptivos si es necesario.
   - Aplica el principio de responsabilidad única en los métodos.
   - Corrige posibles errores o malas prácticas detectadas.
4. **Incluye comentarios en el código refactorizado explicando los cambios realizados.**
5. **Entrega:**
   - El código refactorizado en un archivo `.java`.
   - Un breve informe (puede ser en comentarios o en un documento aparte) justificando las mejoras aplicadas.

### Evaluación
Se valorará la correcta identificación de los problemas, la calidad de la refactorización, la claridad de los comentarios y la justificación de las mejoras aplicadas.
