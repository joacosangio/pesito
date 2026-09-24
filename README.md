# Pesito

Proyecto integrador de la materia **Programación Web I** — Tecnicatura Universitaria en Programación de Sistemas (UCES).

La idea de "Pesito" es poder llevar un registro de los gastos que realizamos en el día a día y poder organizar nuestras finanzas y no perder el trackeo de nuestros gastos. Hacer esto nos ayuda a reconocer el famoso gasto hormiga, gastos innecesarios y sobre todo, ayudarnos a ahorrar para cumplir nuestras metas.

## Autor

Joaquín Sangiorgi

## Estados del proyecto

- **Fase 1** — Planificación, diseño funcional y estructura HTML5 semántica
- **Fase 2** — Maquetación, estilos (CSS3) y diseño responsive
- **Fase 3** — Interactividad y lógica de cliente (JavaScript)

## Estructura del proyecto

```
pesito/
├── index.html              (Slogan + login / registro)
├── inicio.html              (Home con accesos rápidos)
├── gastos.html              (Carga de gastos + historial)
├── ingresos.html            (Carga de ingresos + historial)
├── ahorros.html             (Meta de ahorro)
├── reportes.html            (Informes y contacto)
├── recursos/
│   ├── style.css             (Hoja de estilos externa unificada)
│   ├── funciones.js           (Lógica de comportamiento JavaScript)
│   └── imagenes/               (Recursos multimedia)
├── planificacion/
│   └── PLANIFICACION.md        (Documentación técnica y funcional)
└── README.md
```

## Cómo correr el sitio localmente (MAMP / Apache)

1. Instalar [MAMP](https://www.mamp.info/) (o cualquier servidor Apache local).
2. Copiar (o linkear) la carpeta `pesito/` dentro de la carpeta raíz del servidor local (`htdocs` en MAMP).
3. Iniciar los servidores desde el panel de MAMP.
4. Abrir el navegador en `http://localhost/pesito/index.html`.

No requiere backend, base de datos, ni instalación de dependencias: es un sitio 100% estático del lado del cliente.
