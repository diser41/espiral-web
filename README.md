# Espiral · Lecturas de cartas

Sitio web de **Espiral**: lecturas de cartas para ver tu situación desde otro lugar.
Puerto Montt · Maullín · Calbuco · Online.

> *Tu pregunta, vista desde otro lugar.* No predigo tu futuro. Te ayudo a ver lo que hoy no estás viendo y qué puedes hacer con eso.

Es una sola página estática (`index.html`) con HTML, CSS y JavaScript en el mismo archivo. No necesita instalar nada: se abre directo en el navegador o se publica con GitHub Pages.

---

## Contenido

- [Estructura del proyecto](#estructura-del-proyecto)
- [Secciones de la página](#secciones-de-la-página)
- [Identidad visual](#identidad-visual)
- [Animaciones e interacción](#animaciones-e-interacción)
- [Cómo editar el contenido](#cómo-editar-el-contenido)
- [Ver la página en tu computador](#ver-la-página-en-tu-computador)
- [Publicar con GitHub Pages](#publicar-con-github-pages)
- [Subir cambios](#subir-cambios)
- [Accesibilidad y diseño adaptable](#accesibilidad-y-diseño-adaptable)
- [Ideas pendientes](#ideas-pendientes)

---

## Estructura del proyecto

```
espiral-web/
├── index.html   ← toda la página: contenido, estilos (<style>) y comportamiento (<script>)
└── README.md    ← este documento
```

Dentro de `index.html` el orden es:

1. `<head>`: título, descripción para buscadores y carga de fuentes desde Google Fonts.
2. `<style>`: colores, tipografías, diseño y animaciones.
3. `<body>`: el contenido, sección por sección.
4. `<script>` al final: animaciones al hacer scroll, menú, cartas que giran y botón flotante.

## Secciones de la página

| Orden | Sección | `id` / clase | Qué contiene |
|---|---|---|---|
| — | Encabezado | `.top` | Logo con espiral, menú (Lecturas, Temas, Reserva) y botón de WhatsApp. Queda fijo arriba. |
| 1 | Portada | `#hero` | Frase principal, ciudades, botón para agendar y espiral animada. |
| 2 | Cómo trabajo | `#como` | Taza de té con la frase de bienvenida y las 3 ideas de trabajo. |
| 3 | Lecturas | `#lecturas` | Las tres lecturas con su duración y precio. |
| 4 | Temas | `#temas` | 8 cartas que se dan vuelta y muestran una pregunta para empezar. |
| 5 | El giro | `.giro` | Ejemplos de preguntas reformuladas ("En vez de… / Prueba con…"). |
| 6 | Reserva | `#reserva` | Los 4 pasos para reservar y el botón de WhatsApp. |
| — | Pie de página | `.pie` | Aviso (solo mayores de 18, no reemplaza terapia), logo y ciudades. |
| — | Botón flotante | `#flotante` | "Agenda tu hora": aparece al bajar y se oculta en la sección de reserva. |

### Precios actuales

| Lectura | Detalle | Precio |
|---|---|---|
| Lectura express | 3 cartas · una pregunta puntual · 20 min | $7.000 |
| Análisis de un tema *(la más pedida)* | 7 cartas · amor, trabajo, familia, estudios… · 45 a 60 min | $15.000 |
| Lectura profunda | Varios temas + resumen escrito · hasta 90 min | $25.000 |

Presencial, por videollamada o con audios por WhatsApp. Mismo precio.

## Identidad visual

Estilo **"grimorio del sur"**: papel envejecido, madera, tinta y detalles en lavanda.

### Colores

Están definidos como variables al inicio del `<style>` (`:root`). Si cambias una variable, cambia en toda la página.

| Variable | Color | Uso |
|---|---|---|
| `--bg` | `#F4EEE3` | Fondo papel |
| `--surface` | `#FBF7F0` | Tarjetas |
| `--surface-2` | `#EEE7F6` | Tarjeta destacada (lavanda suave) |
| `--surface-alt` | `#EDE4D3` | Secciones alternas |
| `--line` | `#D9CDB8` | Bordes |
| `--text` | `#2A2420` | Texto principal (tinta) |
| `--muted` | `#6B5E52` | Texto secundario |
| `--accent` | `#6E5A9E` | Lavanda profundo: títulos destacados, precios |
| `--lav` | `#C3B3E6` | Lavanda claro: botones, espiral |
| `--wood` | `#2E2620` | Madera: encabezado, portada, reserva, pie |
| `--cream` | `#F4EEE3` | Texto sobre madera |
| `--amber` | `#F2C98A` | Luz de vela y motas de luz |

### Tipografías

- **Cormorant Garamond**: títulos, frases en cursiva y precios.
- **Karla**: textos, botones y menú.

Se cargan desde Google Fonts, así que necesitan conexión a internet. Sin conexión el navegador usa una letra de reemplazo (tipo Times o Arial).

### La espiral

El logo y la decoración son una espiral dibujada en SVG (no es una imagen). Aparece en el encabezado, en la portada (grande y animada), en la sección de reserva (de fondo) y en el pie de página.

## Animaciones e interacción

| Elemento | Qué hace |
|---|---|
| Espiral de la portada | Se dibuja sola al abrir la página, luego gira muy lento; el punto central late. |
| Luz de vela | Resplandor ámbar que parpadea detrás de la portada. |
| Motas de luz | Puntitos dorados y lavanda que flotan hacia arriba en la portada (se crean con JavaScript). |
| Textos de la portada | Entran uno tras otro al cargar. |
| Botones de WhatsApp | Un brillo los cruza cada pocos segundos; se levantan al pasar el mouse. |
| Taza de té | Vapor animado. |
| Contenido en general | Aparece suavemente al hacer scroll (clase `reveal`). |
| Tarjetas de precio | Se levantan e inclinan levemente al pasar el mouse. |
| Cartas de temas | Se dan vuelta al pasar el mouse, al tocarlas en el celular o con Enter. |
| El giro | La pregunta original se tacha y aparece la reformulada. |
| Encabezado | Se achica y toma sombra al bajar. |
| Menú | Baja suavemente a cada sección y marca en cuál estás. |
| Botón flotante | Aparece después de la portada; se oculta en la sección de reserva. |

**Si la persona tiene activada la opción del sistema "reducir movimiento"**, todas las animaciones se desactivan y la página se muestra quieta y completa.

## Cómo editar el contenido

Abre `index.html` con cualquier editor de texto (por ejemplo, Visual Studio Code o el Bloc de notas) y usa **Buscar** (`Ctrl + F`) para encontrar el texto que quieres cambiar.

### Cambiar un precio

Busca el precio actual, por ejemplo `$15.000`, y reemplázalo. Cada lectura se ve así:

```html
<article class="precio reveal" style="--i:0">
  <div><h3>Lectura express</h3><p>3 cartas · una pregunta puntual · 20 min</p></div>
  <strong>$7.000</strong>
</article>
```

La lectura con la etiqueta "La más pedida" es la que tiene la clase `destacado`.

### Cambiar el número de WhatsApp

El número aparece como texto y en los enlaces `https://wa.me/56964222825`. Busca `56964222825` y reemplaza **todas** las apariciones (enlaces), y luego busca `6422 2825` para el texto visible.

En los enlaces el número va sin `+`, sin espacios y con el código de país (`56`).

### Agregar o quitar una ciudad

Las ciudades aparecen en 4 lugares. Busca `Calbuco` para encontrarlos:

1. La descripción para buscadores (`<meta name="description">`).
2. Las pastillas de la portada (`<ul class="chips">`).
3. El paso 2 de la reserva.
4. El pie de página.

### Cambiar un tema o su pregunta

Cada carta tiene un frente (tema) y un dorso (pregunta):

```html
<div class="carta reveal" style="--i:0" tabindex="0" role="button" aria-label="Amor: ver pregunta"><div class="carta-in">
  <div class="cara frente"><h3>Amor</h3><p>Lo que necesito y no pido</p><small>Girar ↻</small></div>
  <div class="cara dorso"><span>Para empezar</span><p>¿Qué estás cultivando en tus relaciones?</p></div></div></div>
```

Si cambias el nombre del tema, actualiza también el `aria-label`.

### Sobre `style="--i:0"`

Ese número controla el orden en que aparecen los elementos al hacer scroll (0 aparece primero, 1 después, etc.). Si agregas un elemento nuevo en un grupo, dale el número siguiente.

## Ver la página en tu computador

Haz doble clic en `index.html` y se abre en el navegador. No necesita servidor.

## Publicar con GitHub Pages

1. En el repositorio, entra a **Settings → Pages**.
2. En **Source** elige **Deploy from a branch**, rama `main`, carpeta `/ (root)`, y presiona **Save**.
3. En uno o dos minutos la página queda en **https://diser41.github.io/espiral-web/**

Cada vez que subas cambios a `main`, la página publicada se actualiza sola.

Para usar un dominio propio (por ejemplo `espiral.cl`), se configura en la misma pantalla, en **Custom domain**.

## Subir cambios

La conexión con GitHub usa una llave SSH (`~/.ssh/id_ed25519`), registrada en la cuenta **diser41**.

Después de editar `index.html`:

```bash
git add index.html
git commit -m "Describe aquí el cambio"
git push
```

Para comprobar que la conexión funciona:

```bash
ssh -T git@github.com
```

Debe responder *"Hi diser41! You've successfully authenticated…"*.

## Accesibilidad y diseño adaptable

- **Celular:** el diseño se reorganiza bajo 860 px y 560 px de ancho. Las tarjetas pasan a una columna, el menú se oculta (queda el botón de WhatsApp) y los botones apilan el texto y el número.
- **Teclado:** las cartas de temas se pueden girar con `Tab` + `Enter`.
- **Lectores de pantalla:** las decoraciones (espirales, taza, motas) están marcadas como `aria-hidden` y las cartas tienen `aria-label`.
- **Movimiento reducido:** respeta la preferencia `prefers-reduced-motion`.
- **Sin JavaScript:** todo el contenido se ve igual; solo se pierden las animaciones.

## Ideas pendientes

- [ ] Incluir las fuentes dentro del proyecto para que no dependan de internet.
- [ ] Menú desplegable para celular.
- [ ] Código QR de WhatsApp en la sección de reserva.
- [ ] Foto de la gatita negra en la portada.
- [ ] Calendario de citas en línea (por ejemplo Cal.com o Google Calendar) integrado en la sección de reserva.
- [ ] Opiniones reales de consultantes, con permiso.
