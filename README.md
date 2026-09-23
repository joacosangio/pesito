# MisFinanzas

Proyecto integrador de la materia **Programación Web I** — Tecnicatura Universitaria en Programación de Sistemas (UCES).

Sitio web multipágina para el registro de ingresos y gastos personales, definición de metas de ahorro y visualización de informes, desarrollado en HTML5, CSS3 y JavaScript (Vanilla JS) a lo largo de 3 fases de cursada.

## Autor

Joaquín Sangiorgi

## Estado del proyecto

- [x] **Fase 1** — Planificación, diseño funcional y estructura HTML5 semántica
- [ ] **Fase 2** — Maquetación, estilos (CSS3) y diseño responsive
- [ ] **Fase 3** — Interactividad y lógica de cliente (JavaScript)

Ver el detalle de la planificación en [`planificacion/PLANIFICACION.md`](planificacion/PLANIFICACION.md) y los bocetos de pantalla en [`planificacion/wireframes.html`](planificacion/wireframes.html).

## Estructura del proyecto

```
mis-finanzas-web/
├── index.html              (Landing + acceso)
├── dashboard.html           (Registro de movimientos)
├── reportes.html             (Metas de ahorro, informes y contacto)
├── recursos/
│   ├── style.css             (Hoja de estilos externa unificada)
│   ├── funciones.js           (Lógica de comportamiento JavaScript)
│   └── imagenes/               (Recursos multimedia)
├── planificacion/
│   ├── PLANIFICACION.md        (Documentación técnica y funcional)
│   └── wireframes.html          (Bocetos desktop/mobile de las 3 páginas)
└── README.md
```

## Cómo correr el sitio localmente (MAMP / Apache)

1. Instalar [MAMP](https://www.mamp.info/) (o cualquier servidor Apache local).
2. Copiar (o linkear) la carpeta `mis-finanzas-web/` dentro de la carpeta raíz del servidor local (`htdocs` en MAMP).
3. Iniciar los servidores desde el panel de MAMP.
4. Abrir el navegador en `http://localhost/mis-finanzas-web/index.html`.

No requiere backend, base de datos, ni instalación de dependencias: es un sitio 100% estático del lado del cliente.
