# Planificación técnica — MisFinanzas

**Proyecto Integrador de Cursada — Programación Web I (UCES)**
**Fase 1: Planificación, Diseño Funcional y Estructura HTML5**
**Autor:** Joaquín Sangiorgi

---

## Sección I: Planificación y Análisis Funcional

### 1. Propósito y Propuesta de Valor

La mayoría de las personas no lleva un registro sistemático de sus ingresos y gastos personales, lo que dificulta saber en qué se gasta el dinero mes a mes, cumplir metas de ahorro o anticipar problemas financieros. Las soluciones existentes suelen requerir registro de cuentas bancarias, suscripciones pagas o son demasiado complejas para un uso cotidiano simple.

**MisFinanzas** resuelve este problema ofreciendo una herramienta liviana y de uso inmediato para registrar movimientos financieros (ingresos y gastos), definir metas de ahorro concretas y visualizar informes simples del propio comportamiento financiero, sin necesidad de vincular cuentas bancarias reales ni pagar una suscripción.

### 2. Objetivos del Sistema

**Objetivo general:**
Brindar una plataforma web simple que permita a una persona registrar y visualizar su actividad financiera personal (ingresos, gastos y metas de ahorro) de forma rápida y clara.

**Objetivos específicos:**

1. Permitir el registro estructurado de movimientos financieros (monto, categoría, fecha y tipo).
2. Permitir la definición de una meta de ahorro y el seguimiento visual de su progreso.
3. Generar un informe visual simple que compare ingresos y gastos a lo largo del tiempo.
4. Garantizar que la interfaz sea utilizable tanto en computadoras de escritorio como en dispositivos móviles.

### 3. Público Objetivo (User Personas)

**Persona 1 — "Martina, 24 años, trabajadora en relación de dependencia"**
Recibe su sueldo mensual y algunos ingresos extra ocasionales. Quiere entender en qué se le va la plata a fin de mes y ahorrar para un viaje. Usa el celular la mayor parte del tiempo → **prioriza una navegación mobile fluida y carga rápida de datos**.

**Persona 2 — "Joaquín, 23 años, estudiante y trabajador independiente"**
Tiene ingresos variables (changas, proyectos freelance) y gastos irregulares. Necesita una forma rápida de anotar movimientos sueltos sin fricción, generalmente desde la notebook. → **prioriza formularios cortos, rápidos de completar, con validación clara de errores**.

**Persona 3 — "Roberto, 55 años, usuario con poca familiaridad tecnológica"**
Quiere empezar a controlar sus gastos pero se frustra con aplicaciones complejas. → **prioriza una interfaz simple, textos claros, botones grandes y mensajes de error entendibles (no técnicos)**.

Estos tres perfiles influyen directamente en decisiones de usabilidad: formularios cortos con validación visual inmediata, textos en lenguaje simple, navegación de máximo 3 secciones, y diseño mobile-first que se resuelve en la Fase 2.

### 4. Alcance Funcional de las Páginas

| Página | Contenido y funcionalidad |
|---|---|
| **`index.html`** | Landing con la propuesta de valor del sitio y un formulario de acceso (login simulado del lado del cliente, sin backend real). Punto de entrada obligatorio del sitio. |
| **`dashboard.html`** | Página principal funcional: resumen de saldo/ingresos/gastos del mes, formulario para registrar un nuevo movimiento (monto, descripción, categoría, fecha, tipo), y un historial de movimientos con buscador. |
| **`reportes.html`** | Definición y seguimiento de metas de ahorro, informe visual comparando ingresos y gastos por mes, y un formulario de contacto/soporte. |

### 5. Justificación Tecnológica

El proyecto respeta la separación de responsabilidades del desarrollo web del lado del cliente:

- **HTML (estructura):** define el contenido y la semántica de cada página — qué es un encabezado, qué es un formulario, qué es una tabla de datos — independientemente de cómo se ve o se comporta.
- **CSS (presentación):** centralizado en `recursos/style.css`, es el único responsable de la apariencia visual (colores, tipografía, distribución en pantalla, adaptabilidad a distintos tamaños de pantalla). El HTML no contiene atributos de presentación (`style=""`, `<font>`, etc.).
- **JavaScript (comportamiento):** centralizado en `recursos/funciones.js`, es el único responsable de la lógica de interacción (validaciones en tiempo real, menú móvil, cálculo de metas, renderizado dinámico del historial e informes). El HTML no contiene manejadores de eventos inline (`onclick`, `onsubmit`).

Esta separación permite que cada archivo pueda modificarse de forma independiente sin romper a los otros dos, y es exactamente el criterio que se aplica fase a fase: la Fase 1 entrega solo estructura, la Fase 2 agrega estilo, y la Fase 3 agrega comportamiento.

> **Nota sobre el login:** dado que esta materia cubre exclusivamente tecnologías del lado del cliente (no hay servidor de aplicación ni base de datos), el "login" de `index.html` es una simulación: valida el formulario y persiste los datos localmente en el navegador (`localStorage`), pero no constituye un mecanismo de autenticación real. Esta distinción se explicita para la defensa oral.

---

## Sección II: Arquitectura Técnica de Servidores

### Diagrama de Arquitectura Cliente-Servidor

```
   ┌──────────────────────┐                                   ┌───────────────────────────┐
   │        CLIENTE        │                                   │      SERVIDOR (Apache)      │
   │    (Navegador Web)     │                                   │         vía MAMP             │
   │                         │                                   │                               │
   │  HTML + CSS + JS        │──────  Petición HTTP (GET)  ─────▶│  Localiza el recurso en el    │
   │  (index/dashboard/      │        http://localhost/...       │  árbol de directorios         │
   │   reportes .html)       │                                   │  (htdocs/mis-finanzas-web/)   │
   │                         │◀─────  Respuesta HTTP (200 OK)  ──│                               │
   │  Renderiza el DOM y      │        + archivo solicitado       │  Devuelve el archivo tal cual  │
   │  ejecuta funciones.js    │        (.html / .css / .js /      │  (sitio estático, sin lógica   │
   │                         │         imágenes)                 │  de servidor ni base de datos) │
   └──────────────────────┘                                   └───────────────────────────┘
```

**Ciclo de petición y respuesta:**

1. El usuario ingresa `http://localhost/mis-finanzas-web/index.html` en el navegador (cliente).
2. El navegador envía una **petición HTTP GET** al servidor Apache local (levantado por MAMP), solicitando ese recurso.
3. Apache localiza el archivo en el árbol de directorios del proyecto y responde con un código de estado **200 OK** junto con el contenido del archivo (HTML).
4. El navegador parsea el HTML, y por cada recurso enlazado (`style.css`, `funciones.js`, imágenes) repite el ciclo: nueva petición GET → nueva respuesta del servidor.
5. Una vez recibidos todos los recursos, el navegador construye el DOM, aplica los estilos y ejecuta el JavaScript. Toda la lógica de interacción posterior (validaciones, cálculos, `localStorage`) ocurre **enteramente del lado del cliente**, sin nuevas peticiones al servidor.

Al ser un sitio estático, el servidor Apache actúa únicamente como distribuidor de archivos (no hay procesamiento server-side, ni base de datos, ni sesiones de servidor).

### Árbol de Directorios

```
mis-finanzas-web/
├── index.html                  (Punto de entrada obligatorio del sitio)
├── dashboard.html               (Página secundaria — registro de movimientos)
├── reportes.html                  (Página secundaria — metas, informes y contacto)
├── recursos/
│   ├── style.css                   (Hoja de estilos CSS externa unificada)
│   ├── funciones.js                  (Script lógico de comportamiento JavaScript)
│   └── imagenes/                       (Archivos multimedia e iconos)
├── planificacion/
│   ├── PLANIFICACION.md                 (Este documento)
│   └── wireframes.html                    (Bocetos desktop / mobile)
└── README.md
```

---

## Vocabulario técnico de referencia (para la defensa oral)

- **Petición / respuesta HTTP:** ciclo de comunicación cliente-servidor descripto arriba.
- **Elemento inline vs. block:** los elementos *block* (`<section>`, `<div>`, `<p>`) ocupan todo el ancho disponible y generan salto de línea; los *inline* (`<a>`, `<span>`, `<label>`) solo ocupan el espacio de su contenido y no rompen el flujo del texto.
- **Metadatos:** información sobre la página que no se renderiza visualmente pero es leída por el navegador o buscadores (`<meta charset>`, `<meta name="viewport">`, `<meta name="description">`).
- **Semántica:** uso de etiquetas HTML que describen el significado del contenido (`<header>`, `<nav>`, `<main>`, `<footer>`) en lugar de contenedores genéricos sin significado (`<div>` para todo).
