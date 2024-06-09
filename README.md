# Proyecto de Asignación de Tareas a Procesadores

Este proyecto implementa dos algoritmos para la asignación de tareas a procesadores: un algoritmo Greedy (voraz) y un algoritmo Backtracking (de retroceso). El objetivo es probar ambos métodos y comparar sus resultados.

## Estructura del Proyecto

### Paquetes y Clases

- **org.example.Main**: Clase principal que ejecuta los algoritmos de asignación de tareas.
- **Entidad**:
  - **Procesador**: Clase que representa un procesador.
  - **Tarea**: Clase que representa una tarea.
- **Solucionadores**:
  - **Backtracking**: Implementación del algoritmo de retroceso para la asignación de tareas.
  - **Greedy**: Implementación del algoritmo voraz para la asignación de tareas.
  - **SolucionadorAbstracto**: Clase abstracta que define la estructura básica de los solucionadores.

### Archivos de Datos

- **./datasets/Procesadores.csv**: Archivo CSV que contiene la información sobre los procesadores.
- **./datasets/Tareas.csv**: Archivo CSV que contiene la información sobre las tareas.

## Instrucciones de Uso

1. **Preparar el entorno**: Asegúrate de tener los archivos `Procesadores.csv` y `Tareas.csv` en la carpeta `datasets` en el directorio raíz del proyecto.

2. **Ejecutar el proyecto**: La clase `Main` es el punto de entrada del programa. Puedes ejecutarla para probar los algoritmos Greedy y Backtracking.

### Ejemplo de Ejecución

```java
package org.example;

import Entidad.Procesador;
import Entidad.Tarea;
import Solucionadores.Backtracking;
import Solucionadores.Greedy;
import Solucionadores.SolucionadorAbstracto;

import java.util.List;

public class Main {
    public static void main(String[] args) {
        testearBacktracking(0);
        testearGreedy(0);

        testearBacktracking(100);
        testearGreedy(100);
    }

    public static void printSolucion(SolucionadorAbstracto s){
        System.out.println(s);
        System.out.println(s.printMetrica() + "\n");
    }

    public static void testearGreedy(int tiempo){
        Servicios servicios = new Servicios("./datasets/Procesadores.csv", "./datasets/Tareas.csv");
        List<Tarea> tareas = servicios.getTareas();
        List<Procesador> procesadores = servicios.getProcesadores();

        Greedy g = new Greedy(procesadores, tareas);
        g.greedy(tiempo);
        printSolucion(g);
    }

    public static void testearBacktracking(int tiempo){
        Servicios servicios = new Servicios("./datasets/Procesadores.csv", "./datasets/Tareas.csv");
        List<Tarea> tareas = servicios.getTareas();
        List<Procesador> procesadores = servicios.getProcesadores();

        Backtracking b = new Backtracking(procesadores, tareas);
        b.backtracking(tiempo);
        printSolucion(b);
    }
}
```

## Descripción de los Métodos

### `testearBacktracking(int tiempo)`

Este método:
1. Carga las tareas y procesadores desde los archivos CSV.
2. Crea una instancia de `Backtracking` con las listas de procesadores y tareas.
3. Ejecuta el método `backtracking` con el parámetro `tiempo`.
4. Imprime la solución obtenida.

### `testearGreedy(int tiempo)`

Este método:
1. Carga las tareas y procesadores desde los archivos CSV.
2. Crea una instancia de `Greedy` con las listas de procesadores y tareas.
3. Ejecuta el método `greedy` con el parámetro `tiempo`.
4. Imprime la solución obtenida.

### `printSolucion(SolucionadorAbstracto s)`

Este método imprime la solución obtenida y la métrica asociada del solucionador proporcionado.

## Requisitos

- Java 8 o superior
- Archivos `Procesadores.csv` y `Tareas.csv` en el directorio `./datasets/`

## Ejecución del Programa

Para ejecutar el programa, compila todas las clases y ejecuta la clase `Main`. Puedes usar cualquier entorno de desarrollo integrado (IDE) como IntelliJ IDEA, Eclipse o NetBeans, o compilar y ejecutar desde la línea de comandos:

```bash
javac -d bin src/org/example/Main.java
java -cp bin org.example.Main
```

## Contribución

Si deseas contribuir a este proyecto, por favor, crea un fork del repositorio, realiza tus cambios y envía un pull request. Asegúrate de seguir las mejores prácticas de codificación y documentar adecuadamente tu código.
