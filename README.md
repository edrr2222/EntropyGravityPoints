# EntropyGravityPoints

[![Powered by Claude](https://img.shields.io/badge/Powered%20by-Claude-D97757)](https://claude.com)

Simulación de partículas en un único archivo HTML (sin build, sin dependencias que instalar) donde cada partícula representa un átomo real de los 118 elementos de la tabla periódica. Nació como un experimento visual y terminó siendo una forma de observar, en vivo, cómo un sistema cerrado tiende hacia el equilibrio — es decir, entropía.

Abrí `GravityPoints.html` directamente en el navegador. No hay servidor ni instalación.

## Qué hace

- Hacé click en el canvas para crear un **punto de gravedad** que atrae partículas; arrastralo, y doble click para colapsarlo.
- Al colapsar del todo, el punto de gravedad randomiza el elemento de **todas** las partículas de golpe — un reinicio ("big bang") que vuelve a poner en juego los 118 elementos.
- Las partículas chocan y, según reglas simplificadas de electronegatividad y estado de oxidación, forman enlaces (o se repelen si son químicamente incompatibles).
- Los elementos pesados (Z ≥ 84) se desintegran con el tiempo, siguiendo un modo real (alfa o beta menos) desde un isótopo representativo — por ejemplo U-238 → Th-234, no un simple "resta 2".
- El panel **"Elementos / compuestos nuevos"** registra la primera vez que aparece cada compuesto o isótopo, con temperatura (dial 0–1 y su conversión a un Kelvin ficticio), tipo de evento y origen. Se puede exportar a CSV con el botón "Exportar a Excel".
- El panel `dat.GUI` (arriba a la derecha) controla temperatura/energía, escala de tiempo (hasta x0.005 para cámara súper lenta), interferencia entre puntos de gravedad, y visibilidad de etiquetas.

## Por qué

La pregunta original era simple: ¿qué pasa si dejás que todos los elementos interactúen libremente durante mucho tiempo? La respuesta, corriendo la simulación miles de frames, es que el ritmo de "descubrimientos" nuevos crece rápido al principio y después se aplana solo: el sistema llega a un estado estable donde ya no pasa nada nuevo, salvo que se lo perturbe desde afuera. Es una forma bastante intuitiva de tocar de cerca la segunda ley de la termodinámica.

## Sobre la precisión

Los datos de química (electronegatividad, estado de oxidación) y de física nuclear (isótopo representativo, modo de desintegración dominante) están **simplificados a propósito** para que la simulación sea jugable y legible, no para servir de referencia científica — especialmente en elementos superpesados, lantánidos y actínidos. Cada elemento tiene un único isótopo y un único modo de desintegración fijo (no una carta de nucleidos completa con ramificaciones), y los enlaces químicos no modelan geometría molecular ni estequiometría real.

## Arquitectura

Todo el código (HTML, CSS, JS ES5 sin frameworks) vive en `GravityPoints.html`: datos de la tabla periódica y reglas simplificadas de química/física nuclear, seguidas de las clases `GravityPoint` y `Particle`, y un bucle de animación que corre la simulación cuadro a cuadro.

La única dependencia externa es [`dat.gui`](https://github.com/dataarts/dat.gui), cargada desde un CDN.
