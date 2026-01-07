# Generador de Haikus con Cadenas de Markov 🌸

## Sobre el Proyecto

Este proyecto es el **Día 2** de mi reto de "30 Días de Python".

El objetivo fue explorar los fundamentos del **Procesamiento de Lenguaje Natural** sin depender de los modernos Modelos Grandes de Lenguaje (LLMs). En su lugar, volví a lo básico: **Cadenas de Markov**.

Este script ingiere un cuerpo de texto (una colección de Haikus) y genera poemas nuevos y originales prediciendo probabilidades de palabras, mientras se adhiere estrictamente a la estructura tradicional de **5-7-5 sílabas**.

## Cómo Funciona

El algoritmo utiliza una **Cadena de Markov de Segundo Orden**. Esto significa que mira las dos últimas palabras para determinar el contexto.

### El Flujo del Algoritmo:

1. **Ingesta:** Lee el archivo `haikus.txt` y recibe el texto.
2. **Entrenamiento:** Construye un diccionario donde las claves son pares de palabras (`palabra_A`, `palabra_B`) y los valores son listas de posibles `siguiente_palabra`.
3. **Generación y Restricción:**
    * Elige una semilla aleatoria.
    * Predice la siguiente palabra.
    * **CRÍTICO:** Verifica el conteo de sílabas de la palabra predicha. Si la palabra rompe la estructura de línea 5-7-5, es rechazada y el modelo reintenta con otra opción.
4. **Fallback:**
    * Si el modelo se queda "arrinconado" (donde no existe una siguiente palabra válida que encaje con el conteo de sílabas restante), realiza un "salto" a un nuevo par de palabras aleatorio del cuerpo para mantener el flujo del poema sin que el programa falle.

## Empezando

### Prerrequisitos
Necesitarás tener Python instalado y la librería `syllables` (o una similar) para realizar el conteo
