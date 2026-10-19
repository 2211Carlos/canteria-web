# DESIGN.md — CanterIA

> Sistema de diseño de CanterIA. La IA debe leerlo ANTES de generar cualquier pantalla, landing o pieza gráfica.
> Leyenda: **[FIJADO]** = decisión tomada · **[WEB]** = valor leído del código real de canteria.es (repo canteria-web) · **[PROPUESTA]** = por validar · **[DEFINIR]** = falta decidir.

---

## 1. Identidad y jerarquía de marca

- **CanterIA** es la marca matriz ("la cabeza de todo"). Los productos (FlotaIA, ValidaIA, ReadyIA, ObrIA…) son nombres de aplicación bajo ella. **[FIJADO]**
- Todo material público lleva el nombre del producto **y** el logo de CanterIA; el logo va en la cabecera. **[FIJADO]**
- Patrón de nombre: el sufijo "IA" va en negrita y en el color de acento (Flota**IA**, Obr**IA**, Valida**IA**). **[WEB]**
- **ValidaIA sustituye a AlbaránIA**: ya no se usa el nombre AlbaránIA en ningún material. **[FIJADO]**
- Posicionamiento: **"Inteligencia artificial aplicada a pymes"**. No limitarlo a "obra y transporte". **[FIJADO]**
- Firma/rol: "Ingeniero civil · CanterIA" (no "Fundador"). **[FIJADO]**
- CanterIA es independiente: no es marca de ningún empleador. **[FIJADO]**
- No nombrar clientes piloto en material público ("una flota real"). **[FIJADO]** (verificado: la web no los nombra)
- Logo: retícula de bloques (cuadrados crema) con un bloque en verde claro. Favicon SVG en línea. **[WEB]**

## 2. Tono y voz

- Español de España. Tuteo profesional. Voz en plural de marca ("Escuchamos", "Cuéntanos"). **[WEB]**
- Directo, técnico, sin humo. Beneficio concreto antes que descripción técnica. Sinceridad ("dónde la IA no merece la pena"). **[WEB]**
- Todo ejemplo ilustrativo se etiqueta como "Ejemplo ilustrativo"; estados honestos: "En piloto", "En pruebas en obra", "En desarrollo". **[WEB]**
- Evitar: "revolucionario", "disruptivo", emojis, exclamaciones.

## 3. Color

### Marca CanterIA (matriz) **[WEB]**
| Token | Valor | Uso |
|---|---|---|
| `--bosque` | `#0f211a` | Cabecera, hero, modo oscuro (fondo) |
| `--verde` | `#1f7a4d` | **Color ancla**: botones, enlaces, acento sobre fondo claro |
| `--verde-claro` | `#5fbf8a` | Acento sobre fondo oscuro (eyebrow, "IA" del logo) |
| `--cal` | `#efebdd` | Crema: texto sobre oscuro |
| `--bg` | `#f4f2e9` | Fondo modo claro |
| `--surface` | `#ffffff` (claro) · `#16302a` (oscuro) | Tarjetas |
| `--border` | `#d9d5c6` (claro) · `#24433a` (oscuro) | Líneas |
| `--text` / `--text-2` | `#0f211a` / `#55645c` (claro) · `#efebdd` / `#a9bdb1` (oscuro) | Texto |

- Hay modo claro y oscuro (`prefers-color-scheme` + `data-theme`). **[WEB]**
- Regla: un solo color ancla (verde). Sin degradados. **[FIJADO]**
- El verde de CanterIA y el de FlotaIA son de la misma familia (`#1f7a4d` vs RAL 6032 ≈ `#237F52`, diferencia mínima). **[WEB]**
- Para **texto** sobre fondo claro usar `#1f7a4d` (contraste 4,74:1). El RAL 6032 literal (`#237F52`) queda en 4,43:1 y no pasa AA en texto pequeño. **[FIJADO]**

### Acentos por producto **[FIJADO]**
Cada producto tiene su propio acento. La cabecera, el logo y el pie de CanterIA siguen siempre en verde y bosque; el acento del producto solo aparece dentro de su sección o landing. Los colores de estado (cian, ámbar, rojo) **nunca** se usan como acento de producto.

| Producto | Token | Sobre fondo claro | Sobre fondo oscuro | Fondo de chip (claro / oscuro) |
|---|---|---|---|---|
| FlotaIA | `--verde` | `#1f7a4d` | `#5fbf8a` | `#e6f0e9` / `#1d3a32` |
| ObrIA (azul plano) | `--obria` | `#2f5fb3` | `#8fb1ff` | `#e3eaf7` / `#1b2c4d` |
| ValidaIA (violeta) | `--validaia` | `#6a4cc4` | `#b7a6ff` | `#ece8f8` / `#2a2350` |
| ReadyIA (magenta) | `--readyia` | `#b0338a` | `#f08ccb` | `#f6e4ef` / `#45203a` |

- Contraste del texto de acento: 5,08:1 a 7,91:1 (todos AA). Texto blanco sobre relleno de acento: 5,32:1 a 6,16:1.
- Solo el sufijo "IA" del nombre y los chips toman el acento; botones y estructura siguen en verde salvo dentro de la landing del producto.
- Azul y violeta son cercanos: los distinguen el nombre y el logo, no solo el color.
- Un solo acento por producto, más neutros. Sin degradados.

### Estados (comunes a todos los productos)
Cada estado tiene dos variantes: una para **fondo oscuro** (bosque) y otra para **fondo claro**, porque los tonos vivos no se leen sobre crema.

| Estado | Sobre fondo oscuro | Sobre fondo claro | Nota |
|---|---|---|---|
| `--ok` | cian `#3fc6d9` **[WEB]** (8,21:1) | cian oscuro `#0b6e83` (5,24:1) **[PROPUESTA]** | Cian, no verde **[FIJADO]** |
| `--warning` | ámbar `#f0b94a` **[WEB]** (9,37:1) | ámbar oscuro `#8a5a00` (5,28:1) **[PROPUESTA]** | |
| `--danger` | rojo `#f0766b` (5,99:1) **[PROPUESTA]** | rojo `#b42318` (5,86:1) **[PROPUESTA]** | Aún no se usa en la web |
| `--info` | **[DEFINIR]** | **[DEFINIR]** | |

Regla: el estado nunca se comunica solo con color; va siempre con texto o icono ("En ruta", "Retraso 25 min", "Incidencia").

Contraste mínimo WCAG AA (4,5:1 texto, 3:1 UI). Medido en la web: texto 14,95:1 · secundario 5,57:1 · verde sobre claro 4,74:1 · blanco sobre botón 5,32:1 · verde claro sobre bosque 7,43:1.

## 4. Tipografía **[WEB]**

| Rol | Fuente | Pesos |
|---|---|---|
| Titulares y logo | **Source Serif 4** | 600, 700 |
| Cuerpo | **Source Sans 3** | 400, 600, 700 |
| Datos, etiquetas, correo | **DM Mono** | 400, 500 |

- Fuentes **autoalojadas** (carpeta `fonts/`, `font-display: swap`): sin Google Fonts, coherente con RGPD. **[FIJADO]** mantener así.
- Prohibido Inter por defecto. **[FIJADO]**
- Cuerpo 17 px, interlineado 1,55. H1 `clamp(34px, 6.2vw, 58px)`, interlineado 1,04. H2 `clamp(26px, 4.5vw, 38px)`.
- Eyebrow: DM Mono 12 px, mayúsculas, espaciado 0,08em.

## 5. Espaciado, forma y elevación **[WEB]**

- Ancho máximo de contenido: **1080 px**, márgenes laterales 20 px. Móvil primero.
- Esquinas **rectas** en botones, chips y paneles (identidad técnica). Solo los mockups de móvil llevan radio (26 px).
- Sombras solo en mockups de dispositivo. En el resto, bordes finos de 1 px.
- Secciones con respiro vertical amplio (≈ 72 px).

## 6. Componentes

- Botón primario: relleno `--verde`, texto blanco, 1 por vista. Secundario "ghost": contorno crema sobre oscuro. **[WEB]**
- Chip de estado: DM Mono 12 px, fondo `--chip-bg`, texto `--accent-text`. **[WEB]**
- Registro/log: panel DM Mono 13 px con borde izquierdo. **[WEB]**
- Tarjetas: no anidar tarjetas dentro de tarjetas. **[FIJADO]**
- Iconos y escenas: SVG en línea, sin imágenes de stock. **[WEB]**
- Tablas de datos: densas, números a la derecha.
- Formularios: etiqueta visible, errores junto al campo. (La web hoy contacta solo por correo/WhatsApp; si se añade formulario, usar el texto de consentimiento RGPD del proyecto.)

## 7. Movimiento y accesibilidad **[WEB]**

- Aparición al hacer scroll (14 px, 0,6 s) y escenas SVG animadas. Todas respetan `prefers-reduced-motion`.
- Animación con propósito: explicar el ciclo detectar → decidir → actuar → registrar → mejorar.
- Accesibilidad de gráficos: todo SVG informativo lleva `role="img"` y `aria-label` descriptivo; los decorativos, `aria-hidden="true"`. Revisado: 4 escenas informativas con etiqueta y 2 decorativas ocultas. **[WEB]**

## 8. Estructura de canteria.es **[FIJADO]**

Cabecera sticky con logo y navegación: Transporte · Obra · A medida · Método · Quién · Contacto. Oferta en tres bloques separados:
1. **Transporte** — FlotaIA (en piloto).
2. **Automatización en obra** — ObrIA (en pruebas) y ValidaIA (en desarrollo; captura de albaranes, gastos y facturas para gestorías y pymes).
3. **A la medida** — servicio bajo encargo y ReadyIA (en desarrollo).

Después: método de trabajo, "Quién está detrás" y contacto. Pie: Aviso legal y Política de privacidad (publicados). Contacto: carlos@canteria.es.

## 9. Reglas por producto

### FlotaIA
- Color de marca: verde de la familia CanterIA (RAL 6032 ≈ `#237F52`). **[FIJADO]**
- Estado "ok" en cian, nunca verde. **[FIJADO]**
- Tokens en `tokens.css` (rama `identidad-verde`, repo `flotaia-bot`).
- Público: supervisores de operaciones de flota. Lenguaje de dolor concreto.

### ValidaIA (antes AlbaránIA)
- Acento: violeta (`--validaia`). Público: gestorías y pymes.
- Todo material lleva ValidaIA + logo CanterIA. **[FIJADO]**

### ReadyIA / ObrIA
- ReadyIA: acento magenta (`--readyia`).
- ObrIA: acento azul plano (`--obria`). Interfaz principal WhatsApp; los materiales muestran el flujo del mensaje.

## 10. Prohibiciones (anti "diseño de IA")

- Degradados morado-azul genéricos; Inter o fuentes por defecto.
- Tarjetas anidadas y rejillas idénticas sin jerarquía.
- Más de un color ancla por marca.
- Lorem ipsum o claims sin respaldo; imágenes de stock genéricas.
- Nombrar clientes del piloto.
- Cargar fuentes o scripts de terceros sin evaluar RGPD (primero cumplimiento, luego coste).

## 11. Cómo usar este archivo

1. Raíz del repo de cada proyecto, junto a `CLAUDE.md`.
2. En cada producto, copiar las secciones 1–8 y rellenar la 9.
3. Prompt: *"Lee DESIGN.md y respétalo. Si falta un valor [DEFINIR], pregúntame antes de inventarlo."*
4. Cualquier cambio de marca se hace aquí primero y después en el código.
