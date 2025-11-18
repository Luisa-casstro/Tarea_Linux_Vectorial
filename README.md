# Tarea: Cálculo de Masa y Centro de Masa (Integración Triple en C)

**Curso:** Cálculo Vectorial Computacional
**Institución:** Universidad Nacional de Colombia - Departamento de Matemáticas y Estadística
**Autora:** Luisa Castro ([@Luisa-casstro](https://github.com/Luisa-casstro/Tarea_Linux_Vectorial))

---

## 📝 Descripción del Proyecto

Este proyecto es una implementación en **Lenguaje C** de un programa diseñado para calcular la **masa total** ($M$) y el **centro de masa** ($\overline{x}, \overline{y}, \overline{z}$) de un cuerpo tridimensional ($V$) que posee una función de densidad variable $\rho(x,y,z)$.

El objetivo principal es integrar los conceptos del cálculo vectorial (específicamente la integración triple) con la programación numérica y estructurada en C. El programa utiliza métodos de integración numérica (Sumas de Riemann y Monte Carlo) para aproximar las soluciones sobre una región rectangular.

## 📐 Fundamento Teórico

Los cálculos se basan en las definiciones formales de masa y centro de masa mediante integrales triples:

* **Masa Total ($M$):**
    $$M=\iint\iint_{V}\rho(x,y,z)dV$$

* **Centro de Masa ($\overline{x}, \overline{y}, \overline{z}$):**
    $$\overline{x}=\frac{1}{M}\iint\iint_{V}x\rho(x,y,z)dV$$
    $$\overline{y}=\frac{1}{M}\iint\iint_{V}y\rho(x,y,z)dV$$
    $$\overline{z}=\frac{1}{M}\iint\iint_{V}z\rho(x,y,z)dV$$

## ⚙️ Funcionalidades Implementadas

El programa está dividido en módulos para manejar la lógica de integración y las definiciones de densidad de forma separada, tal como se especificó en los requisitos.

### 1. Modelos de Densidad (`densidades.c`)

Se implementaron tres funciones de densidad distintas:

1.  **Densidad Constante:** $\rho(x,y,z)=1$
2.  **Densidad Lineal:** $\rho(x,y,z)=ax+by+cz$
3.  **Densidad Gaussiana:** $\rho(x,y,z)=e^{-(x^{2}+y^{2}+z^{2})}$

### 2. Métodos de Integración Numérica (`integracion.c`)

El programa implementa dos métodos para calcular la integral triple sobre una región rectangular definida por $[x_{min}, x_{max}]$, $[y_{min}, y_{max}]$ y $[z_{min}, z_{max}]$.

1.  **Sumas de Riemann Tridimensional:** Aproxima la integral dividiendo el volumen en $N_x \times N_y \times N_z$ subceldas y evaluando la función en el centro de cada una.
2.  **Método de Monte Carlo:** Estima la integral generando $N$ puntos aleatorios dentro del volumen $V$ y calculando el promedio de la función evaluada en dichos puntos, ponderado por el volumen total.

El usuario puede configurar el número de subdivisiones (para Riemann) o el número total de muestras (para Monte Carlo).

## 📁 Estructura del Proyecto

El código fuente sigue la estructura modular requerida: