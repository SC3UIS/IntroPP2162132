# MPI - Ecuación de calor bidimensional con C

El siguiente repositorio contiene una solución propuesta en mpi con C para la ecuación de calor bidimensional, realizado por PRACE.

### Estructura del repositorio

Los siguientes archivos son los códigos que hacen posible la ecuación, cada uno tiene una función específica, siendo el ***main.c*** el código principal:

- ***core.c***: Contiene el núcleo del código de un solucionador de la ecuación del calor en 2D. Incluye las funciones esenciales para evolucionar la distribución de temperatura en el tiempo, aplicando diferencias finitas para calcular los nuevos valores de temperatura en el dominio 2D. También gestiona la inicialización, el intercambio de datos entre procesadores MPI, y la escritura de resultados.

- ***heat.h***: Este archivo contiene las definiciones de estructuras de datos y funciones relacionadas con la simulación de la ecuación de calor en 2D. Define la estructura field para representar el campo de temperatura y contiene prototipos de funciones que se utilizan en la simulación.

- ***io.c***: Funciones relacionadas con la entrada y salida de datos.

- ***main.c***: Este es el archivo principal del programa. Contiene la función main, que inicia la simulación de la ecuación de calor en 2D utilizando MPI (Message Passing Interface) para la programación paralela. Se encarga de la inicialización, la ejecución de las iteraciones y la finalización de la simulación.

- ***pngwriter.c*** y ***pngwriter.h***: Proporcionan funciones para almacenar los resultados en formato PNG.

- ***setup.c***: Contiene funciones relacionadas con la inicialización de la simulación de la ecuación de calor. Estas funciones leen argumentos de línea de comandos, inicializan el campo de temperatura, y configuran la paralelización de la simulación.

- ***utilities.c***: Este archivo proporciona funciones de utilidad para el manejo de matrices, copia de campos de temperatura y asignación de memoria. Estas funciones facilitan la gestión de los datos y el intercambio de información entre iteraciones.


### Instrucciones de compilación

Proceso de compilación es donde accedemos al entorno MPI, se carga el módulo devtools/mpi/openmpi/3.1.4, se realiza la limpieza y por último, la compilación.

![](/Entrega_MPI/images/compilacion.PNG "")

### Instrucciones de ejecución

#### 1. Modo Interactivo

Predeterminado:

![](/images/ejec1.PNG "")

Desde un archivo:

![](/images/ejec21.PNG "")

Desde un archivo y pasos de tiempo:

![](/images/ejec3.PNG "")

Dimensiones y pasos de tiempo:

![](/images/ejec4.PNG "")

#### 2. Modo Pasivo (sbatch)

Crear el archivo .sh y enviar el trabajo a slurm

![](/images/sbatch.PNG "")

### Pruebas sin mejoras de código

![](/images/sin1.PNG "")

![](/images/sin2.PNG "")

![](/images/sin3.PNG "")

### Pruebas con mejoras de código

![](/images/mejora.PNG "")

### Conclusiones

La versión del código que ha sido adaptada para ejecución paralela ha logrado disminuir de manera considerable los tiempos de procesamiento en comparación con la versión original.

En particular, el rendimiento de la aplicación se ha optimizado notablemente gracias a la paralelización, lo que ha permitido acelerar la velocidad a la que se obtienen los resultados. Esta mejora es más evidente cuando se trabajan con conjuntos de datos más grandes o se realizan simulaciones que involucran una mayor cantidad de pasos de tiempo. La ventaja de esta versión paralelizada radica en su capacidad para dividir la carga de trabajo de manera equitativa entre varios procesadores o nodos, lo que evita cuellos de botella y garantiza una utilización más eficiente de los recursos disponibles.
