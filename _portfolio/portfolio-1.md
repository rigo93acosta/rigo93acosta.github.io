---
title: "Rendimiento en consumo de potencia del vuelo de Drones"
excerpt: "Este artículo presenta un análisis detallado del rendimiento de vuelo de drones, enfocándose en el consumo de potencia durante diferentes tipos de movimiento: horizontal, ascenso, descenso y hovering. Se derivan y explican las ecuaciones fundamentales para calcular la potencia requerida en cada caso, basadas en referencias reconocidas de la literatura aeronáutica. Además, se muestran resultados de simulaciones que ilustran cómo varía el consumo de potencia en función del número de rotores y la velocidad de vuelo, proporcionando información valiosa para el diseño y operación eficiente de drones multirrotor."
collection: portfolio
---

# Potencia de Movilidad

La potencia consumida por movimiento horizontal se calcula usando la siguiente ecuación :
$$P_h = P_p + P_I$$
Donde, $$
P_p = \frac{1}{2} \rho C_{D_0} S v_h^3 + \frac{\pi}{4} R N_b \rho c_b C_{D_0} w^3 \beta^4 \left(1 + 3 \left( \frac{v_h}{w \beta} \right)^2 \right)$$
y $$P_I = \frac{T}{R} \sqrt{\frac{\lambda - v_h^2}{2}},$$
$$ \lambda = \sqrt{v_h^4 + \left( \frac{T}{R \pi \rho \beta^2} \right)^2}$$

> Todas las ecuaciones no referenciadas se encuentran en el Capítulo 13 del libro Flight Performance of Fixed and Rotary Wing Aircraft.

Por otra parte, la potencia consumida cuando el dron asciende se puede calcular empleando la siguiente ecuación (derivada de la Ecuación (12.35) del libro):
$$
P_a = \frac{T}{2 R} v_a + \frac{T}{2 R} \sqrt{v_a^2 + \frac{2 T}{R \pi \rho \beta^2}}
$$

Mientras que la potencia consumida cuando el dron desciende es la siguiente (derivada de la Ecuación (12.50) del libro):
$$
P_d = \frac{T}{2 R} v_d - \frac{T}{2 R} \sqrt{v_d^2 - \frac{2 T}{R \pi \rho \beta^2}}
$$
En esta última ecuación se debe cumplir el siguiente requisito (ubicado en el primer párrafo de la página 334 del libro):
$$\frac{v_d}{2 v_{hover}} \geq 1$$

Como mínimo, la velocidad de descenso debe ser igual o mayor a 2 veces la velocidad de hovering. La velocidad de hovering se calcula así (derivada de la Ecuación (12.1) del libro):
$$
v_{hover} = \sqrt{\frac{T}{2 \rho \pi \beta^2 R}}
$$
# Potencia de Hovering
Según explica el libro, para calcular la potencia de hovering partimos de la siguiente ecuación:
$$P_{hover} = T v_{hover}$$
Es decir, la potencia es fuerza por velocidad. Incorporando la cantidad de rotores $R$, obtenemos la siguiente ecuación:
$$P_h = \frac{T}{R} \sqrt{\frac{T}{2 \rho \pi \beta^2 R}}$$
Tras un ajuste matemático, se obtiene:
$$P_{hover} = \sqrt{\frac{T^3}{2 \rho \pi \beta^2 R^3}}$$
La ecuación anterior que envié fue:
$$P_{hover} = \sqrt{\frac{T^3}{2 \rho \pi \beta^2 R}}$$

# Resultados de Simulaciones
La siguiente figura muestra el consumo de potencia para cada tipo de movimiento en función del número de rotores, cuando el dron se mueve a una velocidad de 10 m/s.

![Figura1](/images/Velocity_10_UAV.png)


En la próxima figura muestra el cambio en el consumo de potencia para cada tipo de movimiento en función de la velocidad, cuando el dron tiene 4 rotores. Nótese cómo en la figura, el consumo de potencia total aumenta y luego cae. Esto está asociado a la condición para descender: cuando el dron tiene una velocidad mayor que la velocidad de hovering, la potencia necesaria para descender disminuye con la velocidad.

![Figura2](/images/Model_4_UAV.png) 

Se puede observar la similitud de la curva que representa el consumo de potencia por movimiento horizontal con la curva de consumo de potencia del modelo empleado en el artículo [Energy Minimization for Wireless Communication with Rotary-Wing UAV](https://ieeexplore.ieee.org/document/8663615/) y en el artículo [Energy efficiency analysis of Drone Small Cells positioning based on reinforcement learning](https://onlinelibrary.wiley.com/doi/abs/10.1002/itl2.166).