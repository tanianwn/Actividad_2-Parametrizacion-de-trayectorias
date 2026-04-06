# Actividad 2.1: Parametrizacion de trayectorias

## ¿Qué es la parametrización de trayectorias?
La parametrización de trayectorias es un método matemático que permite describir una curva en un espacio (2D o 3D) utilizando una variable independiente común denominada **parámetro**, generalmente denotada como $t$. 

En lugar de definir una variable en función de otra (como $y = f(x)$), tanto $x$ como $y$ se definen de forma independiente respecto a $t$:
* $x = x(t)$
* $y = y(t)$

Esto permite representar figuras complejas que no son funciones simples, donde un mismo valor de $x$ puede tener múltiples valores de $y$.

## Descripción de la Actividad
El objetivo de esta actividad consiste en implementar código en MATLAB que genere diversas trayectorias en un plano bidimensional a partir de ecuaciones paramétricas dadas y apartir de imágenes dadas donde se tendrá que encontrar las variables que formen dichas figuras: 
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
```

### 2. Definición de funciones
Se ingresan las ecuaciones paramétricas. Para figuras cerradas y simétricas, se suele combinar el uso de funciones seno y coseno con diferentes frecuencias.
```matlab
% Cálculo de coordenadas independientes
x = cos(t);
y = sin(3*t);
```

### 3. Generación del gráfico
Se utiliza el comando `comet` para visualizar la trayectoria en tiempo real. 
```matlab
% Visualización de la trayectoria
comet(x, y);
axis equal; 
grid on;
```
## Implementación de los Incisos a) - j)
Para automatizar la generación de los 10 ejercicios de la actividad, se utiliza una estructura de celdas `{}` y funciones anónimas `@(t)`. Esto permite que un solo ciclo `for` procese fórmulas matemáticas distintas sin necesidad de reescribir el código completo cada vez.

---

# Actividad 2.2: Parametrización de trayectorias (Coordenadas Polares)
## Sistema de Coordenadas Polares
A diferencia del sistema cartesiano que define un punto mediante desplazamientos horizontales y verticales ($x$, $y$), el sistema de coordenadas polares determina la posición de un punto en un plano bidimensional basándose en dos parámetros principales:
* El ángulo $\theta$ (theta): Representa la dirección o rotación respecto a un eje de origen.
* El radio $r$: Representa la distancia lineal desde el origen (centro) hacia la dirección dictada por el ángulo.

Para lograr graficar estas trayectorias en matlab, se realiza una transformación trigonométrica directa de polares a cartesianas utilizando las siguientes ecuaciones:
* $x = r \cos(\theta)$
* $y = r \sin(\theta)$

## Descripción de la Actividad
El objetivo de esta actividad consiste en implementar código en MATLAB que genere diversas trayectorias en un plano bidimensional utilizando la lógica de coordenadas polares. A partir de imágenes dadas, se realiza un análisis geométrico para encontrar las amplitudes, frecuencias angulares y pasos que formen las figuras requeridas: 
<p align="center">
  <img src="https://github.com/user-attachments/assets/20494281-43e3-469e-bf19-1e0594125a1f" width="600" alt="Robot Cartesiano 3GDL"/>
</p>

## Explicación del Código
La implementación en MATLAB mediante coordenadas polares se divide en tres fases fundamentales:

### 1. Definición del ángulo $\theta$ 
Se establece el vector del ángulo que indica la rotación o angulo al que se dirige. Para generar polígonos/lineas rectas, se utilizan incrementos o saltos grandes correspondientes a la separación de cada vértice. Para curvas suaves como petalos, se utilizan incrementos muy pequeños.
```matlab
% Para polígonos: saltos discretos (ej. pi/2 para un cuadrado de 4 lados)
theta_poligono = 0 : pi/2 : 2*pi; 

% Para curvas/flores: incrementos
theta_curva = 0 : 0.01 : 2*pi;
```

### 2. Definición del radio $r$
El vector del radio determina qué tan lejos del centro se dibujará el punto o la distancia hacia el angulo. Si la distancia es idéntica en todos los vértices, se utiliza un arreglo constante llamados (`ones`). Si la trayectoria entra y sale del origen, se asigna una función trigonométrica armónica con la formula de $r = A \cos(k\theta)$.

```matlab
% Radio constante: crea un arreglo de 1s con la misma longitud que theta
r_poligono = ones(1, length(theta)); 

% Radio variable: Amplitud de 50 y frecuencia 'k' para el numero a determinar
r_curva = 50 * cos(9*theta);
```

### 3. Transformación y visualización
Para que herramientas de trayectoria dinámica como `comet` funcionen adecuadamente, se multiplican los vectores transpuestos para pasar del entorno polar al cartesiano:

```matlab
% transformación de matriz polar a coordenadas X y Y
x = r .* cos(theta);
y = r .* sin(theta);

% visualizacion
comet(x, y);
