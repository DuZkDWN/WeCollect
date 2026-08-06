# WeCollect — MTGDex

> Gestor de colección y constructor de mazos para TCGs, construido con React + Capacitor para Android e iOS.

---

## ✨ Características principales

### 🃏 Colección
- Añade cartas de **Magic** y **Pokémon** en una sola colección unificada.
- Precios en tiempo real desde **Scryfall** (€ y USD con conversión automática).
- Caché de precios de 24 h para reducir peticiones a la API.
- Filtros avanzados: color, tipo, formato, CMC, precio, condición, idioma y carpeta.
- Organización en **carpetas anidadas**.
- Vista en lista o cuadrícula con imagen de la carta.
- Importación desde **Manabox CSV** y exportación a CSV.
- Cálculo del **valor total de la colección** con ajuste por condición (NM / LP / MP / HP / DMG).
- Detalle completo de cada carta: texto de reglas, maná, legalidades, precios foil y traducción automática al español.

### ⚔️ Constructor de mazos — Magic
- Crea mazos en cualquier formato: Commander, Standard, Modern, Pioneer, Legacy, Vintage, Pauper, Draft.
- Búsqueda de cartas con **autocompletado** vía Scryfall.
- Agrupación automática por tipo: Criaturas, Instantáneos, Conjuros, Encantamientos, Artefactos, Planeswalkers, Tierras.
- Soporte de **Comandante** con selector dedicado y detección desde la lista de cartas.
- Sistema de **Brackets de poder** Commander (B1–B5, basado en las reglas oficiales WotC 2025) con autodetección.
- 📊 **Curva de maná visual** — barras por CMC con gradiente de color, actualización en tiempo real.
- 🏷️ **Badges de rol automáticos** — clasifica cada carta como Ramp, Draw, Removal, Tutor o Combo sin IA externa.
- ⬆️ **Exportación a Moxfield / MTGO** — copia el mazo al portapapeles en formato estándar `N NombreCarta`, compatible con Moxfield, Archidekt y MTGO.
- Organización de mazos en carpetas.

### ◉ Constructor de mazos — Pokémon TCG
- Búsqueda de cartas via **TCG Pokémon API**.
- Control de cantidad con límite de 60 cartas.
- Organización en carpetas.

### ❤️ Contador de vidas
- Soporte para 2–6 jugadores.
- Formatos: Commander (40 PV), Standard (20 PV) y personalizado.
- Seguimiento de **daño de comandante** por oponente.
- Contadores adicionales: veneno, experiencia, energía y maná.
- Indicadores de delta al cambiar vida (+/−).
- Layouts: retrato, paisaje y modo **mesa** (jugadores girados 180° para verse frente a frente).
- Estado de partida persistido en localStorage — sobrevive a cierres accidentales.

### 📷 Escáner de cartas
- OCR client-side con **Tesseract.js** — no envía imágenes a ningún servidor.
- Recorta automáticamente la zona del título y busca en Scryfall.
- Añade cartas a la colección directamente desde el escáner.

### 🎨 Temas visuales
28 temas incluidos basados en el universo de Magic y Pokémon TCG:

| Categoría | Temas |
|---|---|
| Gremios (2 colores) | Azorius, Dimir, Rakdos, Gruul, Selesnya, Orzhov, Izzet, Golgari, Boros, Simic |
| Cuñas (3 colores) | Esper, Grixis, Jund, Naya, Bant, Abzan, Jeskai, Sultai, Mardu, Temur |
| Energías Pokémon | Planta, Fuego, Agua, Rayo, Psíquico, Lucha, Incoloro, Oscuro, Metálico, Dragón, Hada |
| Personalizado | Editor de colores completo con importación desde cualquier tema base |

### 🔔 Actualizaciones automáticas
- Comprueba `version.json` en GitHub 3 segundos tras el arranque.
- Muestra una notificación no intrusiva si hay una versión nueva disponible.

---

## 🛠️ Stack técnico

| Capa | Tecnología |
|---|---|
| UI | React 18 + CSS custom properties |
| Nativo | Capacitor 6 (Android / iOS) |
| APIs externas | Scryfall API, TCG Pokémon API |
| OCR | Tesseract.js (client-side, cargado desde CDN) |
| Persistencia | `localStorage` + Capacitor Filesystem (nativo) |
| Tipografía | Cinzel, Lexend, Roboto Condensed (Google Fonts) |

---


## 🔌 APIs utilizadas

| API | Uso | Límite |
|---|---|---|
| [Scryfall](https://scryfall.com/docs/api) | Datos, precios e imágenes de cartas Magic | 10 req/s (cola interna de 110 ms) |
| [TCG Pokémon API](https://pokemontcg.io/) | Datos e imágenes de cartas Pokémon | Sin autenticación requerida |
| Google Translate (no oficial) | Traducción del texto de reglas al español | Sin garantías de disponibilidad |

> La app respeta los límites de Scryfall mediante una cola global serializada y una caché de 24 horas en `localStorage`.

---

## 📄 Licencia

Este proyecto es de uso personal. Consulta el archivo `LICENSE` si existe o contacta al autor para más información.

---

## 🙏 Créditos

- Datos de cartas Magic: [Scryfall](https://scryfall.com)
- Datos de cartas Pokémon: [TCG Pokémon API](https://pokemontcg.io)
- OCR: [Tesseract.js](https://github.com/naptha/tesseract.js)
- Iconografía de maná: SVG custom basados en los símbolos oficiales de Magic: The Gathering
