# Pesito

Proyecto integrador de la materia **Programación Web I** — Tecnicatura Universitaria en Programación de Sistemas (UCES).

La idea de "Pesito" es poder llevar un registro de los gastos que realizamos en el día a día y poder organizar nuestras finanzas y no perder el trackeo de nuestros gastos. Hacer esto nos ayuda a reconocer el famoso gasto hormiga, gastos innecesarios y sobre todo, ayudarnos a ahorrar para cumplir nuestras metas.

## Enlaces

- **Sitio publicado:** https://joacosangio.github.io/pesito/
- **Wireframes (Figma, desktop y mobile):** https://www.figma.com/design/BIAIYR00IH8I3REvZRtIuV

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
│   └── imagenes/               (Recursos multimedia y capturas)
├── planificacion/
│   └── PLANIFICACION.md        (Documentación técnica y funcional)
├── ENLACES.txt                 (Links al sitio, wireframes y repositorio)
└── README.md
```

## Cómo correr el sitio localmente (MAMP / Apache)

1. Instalar [MAMP](https://www.mamp.info/).
2. Descargar el proyecto: `git clone https://github.com/joacosangio/pesito.git` (o **Code → Download ZIP** en GitHub).
3. En MAMP, ir a **Preferences → Server → Document Root → Select...** y elegir la carpeta `pesito/`. Confirmar con **OK**.
4. En **Preferences → Ports**, verificar que el puerto de Apache sea **80**.
5. Iniciar los servidores (**Start Servers**). Si ya estaban corriendo, detenerlos y volver a iniciarlos para que Apache tome la nueva configuración.
6. Abrir el navegador en `http://localhost/`.

Las capturas de esta configuración están en la Sección II de [`PLANIFICACION.md`](planificacion/PLANIFICACION.md).

No requiere backend, base de datos, ni instalación de dependencias: es un sitio 100% estático del lado del cliente.
