# CORRECCION.md

Este documento detalla las malas prácticas identificadas en el proyecto *clima-app* y las soluciones aplicadas para mejorar la calidad del código, la mantenibilidad y la experiencia del usuario.

---

## ✅ 1. Falta de enlace al archivo CSS personalizado (`styles.css`)

**Problema:**  
El archivo `index.html` no incluía un enlace al archivo de estilos CSS personalizado (`index.css`), lo cual impedía que se aplicaran los estilos visuales definidos.

**Por qué es una mala práctica:**  
El sitio pierde la presentación visual planificada, afectando la experiencia del usuario.

**Solución:**  
Se agregó la siguiente línea dentro de la etiqueta `<head>` del HTML:

```html
<link rel="stylesheet" href="/clima-app/public/index.css">
```

**Beneficios:**  
- Activa la apariencia visual planificada
- Mejora la presentación del proyecto
- Permite reutilizar estilos definidos

## ✅ 2. Uso de estilos inline (style="...") en elementos HTML
**Problema:**  
Se encontraron estilos embebidos directamente en elementos HTML, por ejemplo:
```html
<div class="map-legend__color" style="background-color: #FF0000;"></div>
```

**Por qué es una mala práctica:**  
- Rompe la separación de responsabilidades (HTML ≠ CSS)
- Hace el código menos mantenible y más repetitivo
- Aumenta el riesgo de errores y dificulta cambios globales

**Solución:**  
Se trasladaron estos estilos al archivo CSS, creando clases específicas:

```css
.legend--muy-frio     { background-color: #0000FF; }
.legend--frio         { background-color: #00FFFF; }
.legend--templado     { background-color: #00FF00; }
.legend--calido       { background-color: #FFFF00; }
.legend--muy-calido   { background-color: #FF0000; }
```
Y se usaron así en el HTML:
```html
<div class="map-legend__color legend--muy-frio"></div>
```
**Beneficios:**  
- Código más limpio y escalable
- Estilos reutilizables
- Mejor organización y mantenimiento

## ✅ 3. Falta de comentarios en algunas secciones
**Problema:**  
El código HTML y CSS no incluye comentarios en algunas partes clave

**Por qué es una mala práctica:**  
- Dificulta la comprensión por otros desarrolladores

**Solución:**  
Se agregaron comentarios explicativos en secciones clave, por ejemplo:

```html
<!-- Leyenda visual de temperaturas por colores -->
<div class="map-legend">
```
```css
/* Leyenda de colores para el mapa según la temperatura */
.legend--muy-frio { background-color: #0000FF; } /* < 0°C */
```

**Beneficios:**  
- Facilita el mantenimiento
- Mejora la comunicación en equipos
- Acelera futuras modificaciones y resolución de errores