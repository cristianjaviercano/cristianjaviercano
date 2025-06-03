# Bloque de ejercicios Capitulo Tres

1. **Ejercicios**
   1. **Generador Lehmer:** Implemente un generador de Lehmer con m=127, a=30, y $$X_0​=1$$. Genere los primeros 10 números $$X_i​$$ y los correspondientes $$U_i$$​. ¿Observa algún patrón obvio? (Nota: este es un ejemplo pequeño para ilustración, no un buen generador).
   2. **Prueba de Uniformidad (Chi-cuadrado):** Dada la siguiente secuencia de 20 números supuestamente U(0,1): 0.12, 0.87, 0.34, 0.65, 0.05, 0.48, 0.71, 0.92, 0.23, 0.50, 0.78, 0.19, 0.41, 0.99, 0.02, 0.68, 0.29, 0.58, 0.81, 0.38. Realice una prueba Chi-cuadrado de uniformidad usando k=5 intervalos. Use α=0.05.
   3. **Transformada Inversa (Exponencial):** Derive la fórmula para generar variables aleatorias exponenciales con media μ=10 usando el MTI. Genere 3 observaciones usando $$U_1​=0.25,U_2​=0.50,U_3​=0.75$$.
   4. **Transformada Inversa (Discreta):** Una V.A. discreta X toma valores 1, 2, 3 con probabilidades $$P(X=1)=0.3,P(X=2)=0.5,P(X=3)=0.2$$. Describa cómo generaría observaciones de X usando MTI. Genere 2 observaciones usando $$U_1​=0.45, U_2​=0.85$$.
   5. **Box-Muller:** Usando $$U_1​=0.6 y U_2​=0.3$$, genere un par de variables aleatorias Normales estándar (Z1​,Z2​) usando el método de Box-Muller. Luego, transforme Z\_1​ para que siga una distribución $$N(50,102)$$.
   6. **Aceptación-Rechazo (Conceptual):** Describa conceptualmente cómo podría usar el método de Aceptación-Rechazo para generar variables de una FDP $$f(x)=2x$$ para $$0≤x≤1$$ (y 0 en otro caso), usando una FDP mayorante $$g(x)=1$$ (Uniforme(0,1)). ¿Cuál sería el valor de c? ¿Cuál sería la probabilidad de aceptación?

* **Preguntas para Discusión:**
  1. ¿Por qué se utiliza el término "pseudoaleatorio" en lugar de "aleatorio" para los números generados por computadora? ¿Cuáles son las implicaciones prácticas de esta distinción?
  2. ¿Qué problemas podría causar un generador de números aleatorios con un período corto en una simulación a gran escala de un sistema de producción?
  3. Si una secuencia de números generados pasa la prueba Chi-cuadrado de uniformidad y la prueba de autocorrelación de lag 1, ¿puede concluir que es una secuencia "buena" para cualquier propósito de simulación? ¿Por qué sí o por qué no?
  4. Compare el método de la transformada inversa y el método de aceptación-rechazo en términos de su generalidad, eficiencia y facilidad de implementación. ¿Cuándo preferiría uno sobre el otro?
  5. Explique por qué la reproducibilidad de una secuencia de números pseudoaleatorios es una característica deseable en los estudios de simulación.
