# Actividad 2.1: Parametrizacion de trayectorias

## ¿Qué es la parametrización de trayectorias?
La parametrización de trayectorias es un método matemático que permite describir una curva en un espacio (2D o 3D) utilizando una variable independiente común denominada **parámetro**, generalmente denotada como $t$. 

En lugar de definir una variable en función de otra (como $y = f(x)$), tanto $x$ como $y$ se definen de forma independiente respecto a $t$:
* $x = x(t)$
* $y = y(t)$

Esto permite representar figuras complejas que no son funciones simples, donde un mismo valor de $x$ puede tener múltiples valores de $y$.

## Descripción de la Actividad
El objetivo de esta actividad consiste en implementar código en MATLAB que genere diversas trayectorias en un plano bidimensional a partir de ecuaciones paramétricas dadas y apartir de imágenes dadas donde se tendrá que encontrar las variables que formen dicha figura. 
<p align="center">
  <img src="https://github.com/user-attachments/assets/54b0c0a3-5bb4-428d-a8ed-eb9f4408b3f2" width="600" alt="Robot Cartesiano 3GDL"/>
</p>


## Explicación del Código

La implementación en MATLAB se divide en tres fases fundamentales:

### 1. Definición del parámetro $t$
Se establece el rango de valores que tomará el parámetro. El incremento o "paso" determina la suavidad de la curva y la velocidad de la animación.
```matlab
% Se define el parámetro de tiempo/proyección
% [inicio : incremento : fin]
t = [0 : 0.01 : 2*pi];

### 2. Definición de funciones
Se ingresan las ecuaciones paramétricas. Para figuras cerradas y simétricas, se suele combinar el uso de funciones seno y coseno con diferentes frecuencias.

```matlab
% Cálculo de coordenadas independientes
x = cos(t);
y = sin(3*t);
