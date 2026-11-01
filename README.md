# Dungeon Forge

[![Developed with Gemini](https://img.shields.io/badge/Desarrollado%20con-Gemini-8E75B2?style=flat-square&logo=google&logoColor=white)](https://deepmind.google/technologies/gemini/)
[![License: MIT](https://img.shields.io/badge/Licencia-MIT-amber.svg?style=flat-square)](LICENSE)
[![Zero Build](https://img.shields.io/badge/Arquitectura-Vanilla%20HTML%2FCSS%2FJS-orange?style=flat-square)](#stack-tecnol%C3%B3gico)
[![Offline Ready](https://img.shields.io/badge/Ejecuci%C3%B3n-100%25%20Offline-emerald?style=flat-square)](#instalaci%C3%B3n-y-uso)

**Dungeon Forge** es un estudio web integral diseñado para la generación procedural, edición interactiva y maquetación editorial de cuadernos de exploración de mazmorras listos para imprimir (*Print & Play*). Orientado a juegos de rol en solitario y mecánicas *roll & write*, genera documentos vectoriales en PDF de alta fidelidad directamente desde el navegador, sin necesidad de servidores, registros ni dependencias externas.

> **Aviso de atribución:** Este proyecto ha sido diseñado, programado y estructurado en su totalidad con el soporte técnico y arquitectónico de **Gemini**.

---

## Índice

- [Características Principales](#características-principales)
  - [1. Motor Procedural Determinista](#1-motor-procedural-determinista)
  - [2. Editor Visual Interactivo](#2-editor-visual-interactivo)
  - [3. Constructor y Maquetador de Cuadernos](#3-constructor-y-maquetador-de-cuadernos)
  - [4. Motor de Exportación PDF Vectorial](#4-motor-de-exportación-pdf-vectorial)
  - [5. Persistencia y Privacidad](#5-persistencia-y-privacidad)
- [Stack Tecnológico](#stack-tecnológico)
- [Instalación y Uso](#instalación-y-uso)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Guía de Impresión (A5 sobre Hojas A4)](#guía-de-impresión-a5-sobre-hojas-a4)
- [Licencia](#licencia)

---

## Características Principales

### 1. Motor Procedural Determinista
- **Semillas Reproducibles (PRNG):** Basado en el algoritmo pseudoaleatorio `Mulberry32`. La misma semilla alfanumérica, dimensiones y parámetros garantizan la reproducción idéntica de la estructura, entidades y conexiones entre pisos.
- **5 Algoritmos Reales de Generación:**
  - *Binary Space Partitioning (BSP):* Complejos arquitectónicos regulares y ordenados.
  - *Room & Corridor:* Distribución muestreada de cámaras rectangulares enlazadas mediante pasillos ortogonales en L.
  - *Recursive Backtracking:* Laberintos densos de corredores estrechos con bifurcaciones calculadas.
  - *Random Walk (Drunkard's Walk):* Galerías orgánicas y túneles excavados de aspecto minero.
  - *Cellular Automata:* Grutas y cavernas naturales kársticas basadas en reglas de autómatas celulares.
- **Garantía de Conectividad (BFS):** Cada planta pasa por un validador basado en *Breadth-First Search*. Si la entrada y la salida quedan en componentes conexas aisladas, un agente excavador traza pasillos correctores de forma automática antes de ubicar el mobiliario y las criaturas.

### 2. Editor Visual Interactivo
- Lienzo 2D con cuadrícula configurable, control de zoom y herramientas de dibujo continuo.
- Sistema de **Deshacer (`Undo`) y Rehacer (`Redo`)** con pila de estados.
- Pinceles estructurales: Habitaciones, pasillos, muros, puertas estándar y puertas secretas.
- Catálogo de entidades modificables:
  - **Enemigos:** Puntos de vida (HP), nivel de amenaza, daño y recompensas editables.
  - **Tesoros y Trampas:** Cofres, reliquias, pociones, fosos y glifos rúnicos.
  - **Ambientales:** Fuentes sagradas, altares de intercambio y círculos de teletransporte.
  - **Conexiones Verticales:** Escaleras ascendentes y descendentes vinculadas a plantas específicas.
- Inspector lateral para editar atributos de celdas o entidades en tiempo real.
- Exportación directa de la planta activa a imagen PNG.

### 3. Constructor y Maquetador de Cuadernos
- Reorganización de páginas con previsualización en vivo, ordenación, inserción y duplicado.
- Soporte para distintos tipos de pliegos:
  - Portada temática del cuaderno.
  - Reglas de juego y resolución de turnos.
  - Ficha de personaje con contadores de salud (HP), equipo e inventario.
  - Mapas de planta con cajetín de objetivos y registro de antorchas/turnos.
  - Bestiario y tablas de criaturas.
  - Tablas de tesoros, acontecimientos y pautas para notas.
- Presets rápidos de extensión de cuaderno: 10, 20 o 30 páginas por volumen.

### 4. Motor de Exportación PDF Vectorial
- Generación vectorial pura en el cliente mediante **`pdf-lib`** (sin rasterizado ni pérdida de calidad al imprimir).
- **Formatos soportados:** A4, A5 y Libreta de Bolsillo (3 × 5 pulgadas / 76 × 127 mm).
- **Orientación:** Vertical (*Portrait*) y Horizontal (*Landscape*).
- **Perfiles de Color:** Blanco y Negro puro (alto contraste para trazo a lápiz y ahorro de tóner), Escala de Grises y Color completo.
- Opciones editoriales: Marcas de corte (*crop marks*), numeración automática y leyendas de mapa.

### 5. Persistencia y Privacidad
- Almacenamiento local mediante **IndexedDB** para autoguardado de múltiples proyectos simultáneos.
- Importación y exportación de proyectos completos en formato JSON portable.
- Operatividad 100% *offline*: no recopila telemetría ni realiza llamadas a APIs externas.

---

## Stack Tecnológico

| Capa | Tecnología |
| :--- | :--- |
| **Lenguaje y Entorno** | HTML5, CSS3, JavaScript moderno (ES6+) en archivo autocontenido |
| **Estilos e Interfaz** | Tailwind CSS (CDN) con paleta temática oscura |
| **Iconografía** | Lucide Icons |
| **Generación de Documentos** | PDF-Lib (manipulación y renderizado vectorial directo) |
| **Almacenamiento** | IndexedDB API + LocalStorage |

---

## Instalación y Uso

No requiere Node.js, `npm` ni compiladores. Funciona directamente en cualquier navegador moderno (**Chrome**, **Firefox**, **Edge**, **Brave**):

1. Clona el repositorio o descarga el archivo fuente:
   ```bash
   git clone https://github.com/tu-usuario/dungeon-forge.git
   cd dungeon-forge
   ```
2. Abre el archivo `index.html` (o `dungeon-forge.html`) en tu navegador.
3. Elige una plantilla en el **Dashboard** o configura los parámetros en el **Generador**.
4. Modifica las plantas en el **Editor Visual**, ajusta el orden de hojas en el **Cuaderno** y pulsa **Descargar PDF**.

---

## Estructura del Proyecto

```text
dungeon-forge/
│
├── index.html          # Aplicación autocontenida (UI, motor PRNG, algoritmos, editor y PDF)
├── README.md           # Documentación técnica y guía de uso
└── LICENSE             # Licencia de código abierto MIT
```

---

## Guía de Impresión (A5 sobre Hojas A4)

Para imprimir un cuaderno en tamaño A5 usando folios estándar A4 existen dos métodos según el acabado final deseado:

### Opción 1: Modo Folleto / Cuadernillo (Para doblar por el lomo)
Abre el PDF en tu lector habitual (como Adobe Acrobat Reader o jPDF):
1. Pulsa `Ctrl + P` para abrir el diálogo de impresión.
2. En la sección de diseño de página, selecciona **Folleto** (*Booklet*).
3. Configura la encuadernación en **Izquierda** (*Left binding*) y el subconjunto en **Ambos lados**.
4. En las opciones de doble cara, selecciona **Voltear por el borde corto** (*Flip on short edge*).
5. Al finalizar, dobla todas las hojas por la mitad: las páginas quedarán ordenadas correlativamente para grapar en el pliegue central.

### Opción 2: Dos páginas por hoja (Para cortar con guillotina)
1. Pulsa `Ctrl + P` y elige **Múltiples páginas por hoja** (selecciona **2 páginas por hoja**).
2. Fija la orientación del papel en **Horizontal** (*Landscape*).
3. Si imprimes a doble cara, selecciona **Voltear por el borde largo** (*Flip on long edge*).
4. Corta las hojas A4 por la mitad (a 148,5 mm) y apílalas en orden secuencial para anillar o encuadernar.

---

## Créditos

Este proyecto ha sido desarrollado e implementado en su totalidad con la asistencia de **Gemini**.

---

## Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo [LICENSE](LICENSE) para más detalles.
