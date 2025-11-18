# Tarea: Cálculo de Masa y Centro de Masa (Integración Triple en C)

**Curso:** Cálculo Vectorial Computacional
**Institución:** Universidad Nacional de Colombia - Departamento de Matemáticas y Estadística
**Autora:** Luisa Fernanda Castro Buesaquillo
 ([@Luisa-casstro](https://github.com/Luisa-casstro/Tarea_Linux_Vectorial))

---

Cálculo de Masa y Centro de Masa (Integración Triple en C)

Este repositorio contiene una implementación modular en C para resolver problemas de cálculo vectorial computacional. El programa calcula la masa total y las coordenadas del centro de masa de un sólido, permitiendo elegir entre diferentes densidades y métodos de integración numérica.

📁 Estructura del Proyecto

El código está organizado para separar la lógica matemática de la interfaz de usuario:

triple_integral/
├── src/
│   ├── main.c          # Control del flujo y menús
│   ├── densidades.c    # Definición de funciones de densidad
│   └── integracion.c   # Lógica de Riemann y Monte Carlo
├── include/
│   ├── densidades.h    # Cabeceras de densidades
│   └── integracion.h   # Cabeceras de integración
├── obj/                # Archivos objeto (.o) generados
├── programa_vectorial  # Ejecutable final
└── Makefile            # Automatización de compilación


🧠 Fundamento Teórico

El programa aproxima las siguientes integrales triples sobre una región rectangular $V$:

Masa Total ($M$):


$$M = \iiint_V \rho(x, y, z) \, dV$$

Centro de Masa ($\bar{x}, \bar{y}, \bar{z}$):


$$\bar{x} = \frac{1}{M} \iiint_V x\rho \, dV, \quad \bar{y} = \frac{1}{M} \iiint_V y\rho \, dV, \quad \bar{z} = \frac{1}{M} \iiint_V z\rho \, dV$$

Opciones disponibles

Densidades ($\rho$):

Constante: $\rho = 1$

Lineal: $\rho = x + y + z$

Gaussiana: $\rho = e^{-(x^2 + y^2 + z^2)}$

Métodos: Sumas de Riemann y Monte Carlo (Optimizado).

🔷 Diagrama de Flujo

A continuación se describe la lógica principal del programa, desde la solicitud de datos hasta la generación del archivo CSV.

flowchart TD

    A[Inicio] --> B[Declarar variables]
    B --> C[Solicitar límites x, y, z]
    C --> D[Solicitar método: Riemann o MonteCarlo]
    D --> E[Solicitar tipo de densidad]
    E --> F[Solicitar pasos o muestras N]
    F --> G[Iniciar cronómetro]

    %% Selección de densidad
    G --> H{Tipo de densidad}
    H -->|Constante| H1[Usar densidad constante]
    H -->|Lineal| H2[Usar densidad lineal]
    H -->|Gaussiana| H3[Usar densidad gaussiana]

    H1 --> I[Preparar integración]
    H2 --> I
    H3 --> I

    %% Método
    I --> J{Método seleccionado}

    %% Riemann
    J -->|Riemann| K[Bucle triple i, j, k]
    K --> L[Sumar volumen por rho]

    %% Monte Carlo
    J -->|MonteCarlo| M[Bucle desde 0 a N]
    M --> N[Generar puntos aleatorios]
    N --> O[Acumular promedio por volumen]

    %% Masa
    L --> P[Integración terminada]
    O --> P

    P --> Q[Guardar M]

    %% Momento X (Simplificado para visualización)
    Q --> R[Calcular momentos Mx, My, Mz]
    R --> S[Ejecutar integración para cada momento]
    S --> T[Guardar y Exportar a CSV]


▶️ Compilación y Ejecución

El proyecto incluye un Makefile para facilitar la gestión. Asegúrate de estar en la raíz del proyecto (donde está el archivo Makefile).

1. Compilar

Genera el ejecutable y la carpeta de objetos:

make


2. Ejecutar

Inicia el programa interactivo:

./programa_vectorial


(O usa make run para compilar y ejecutar en un solo paso).

3. Limpiar

Para borrar los archivos compilados y empezar de cero:

make clean


📊 Resultados

Al finalizar la ejecución, se generará (o actualizará) el archivo resultados.csv en el directorio actual. Este formato facilita el análisis de datos en Excel o Python.

Formato del CSV:
Metodo,Densidad,N,M,x_bar,y_bar,z_bar,Tiempo

Ejemplo de salida:

MonteCarlo,Gaussiana,100000,12.5831,0.1020,-0.0030,0.2210,0.0872
Riemann,Lineal,50,250.00,5.00,5.00,5.00,0.1540