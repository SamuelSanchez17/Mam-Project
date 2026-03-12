# Mam Project (MamLingua) — Aplicación iOS para preservación cultural y aprendizaje de idioma

> Aplicación iOS inmersiva enfocada en **preservar, difundir y enseñar la cultura Mam (Chiapas, México)** mediante contenido interactivo, minijuegos y un traductor integrado.  
> Desarrollada con **SwiftUI** y soporte **multiidioma** (Español, Inglés y Mam), incluyendo integración con **Google Cloud Translation API** para traducciones en tiempo real.

---

## 🎯 Descripción del proyecto

**Mam Project** (en la app aparece como *MamLingua*) es una aplicación educativa/cultural que combina:

- **Aprendizaje guiado del idioma Mam** (abecedario, frases y vocabulario).
- **Actividades interactivas** tipo juego para reforzar el aprendizaje.
- **Secciones culturales** (música, gastronomía, tradiciones, etc.) para contextualizar el idioma.
- **Experiencia multiidioma** gestionada desde un `LanguageManager` con archivos JSON por idioma.
- **Traducción en tiempo real** mediante un servicio de traducción conectado a la API de Google.

Este repositorio está pensado como un proyecto demostrativo de:
- Construcción de UI moderna con **SwiftUI**.
- Manejo de estado global con **EnvironmentObject**.
- Arquitectura por vistas + servicios.
- Integración con servicios externos (API REST) desde iOS.

---

## 🏗️ Arquitectura general (alto nivel)

```text
┌──────────────────────────────────────────────┐
│              iOS App (SwiftUI)               │
│  Views / Navigation / Assets / UI State      │
└───────────────────────┬──────────────────────┘
                        │
          ┌─────────────┴─────────────┐
          ▼                           ▼
┌───────────────────────┐   ┌───────────────────────┐
│  Localización (i18n)  │   │ Traducción (API)      │
│  LanguageManager      │   │ TranslationService    │
│  JSON por idioma      │   │ Google Translate API  │
└───────────────────────┘   └───────────────────────┘
                        │
                        ▼
            ┌───────────────────────────┐
            │ Experiencias interactivas │
            │ Lecciones / Juegos        │
            └───────────────────────────┘
```

---

## ✨ Funcionalidades principales

### 🌐 Multiidioma (Español / Inglés / Mam)
- Selector de idioma reutilizable mediante `LanguageSwitcher`.
- Estado global con `LanguageManager` como `ObservableObject`.
- Textos localizados usando llaves (keys) y archivos `*.json` en el bundle.

### 📖 Experiencia guiada tipo “historia”
- Vista de introducción y navegación inicial.
- Lectura tipo “libro” con páginas (`BookView`) y soporte de recursos multimedia (incluye uso de `AVFoundation` para audio).

### 📚 Módulo de lecciones
Agrupa rutas de aprendizaje en una sección tipo “mapa”:
- **Abecedario**: recorrido por letras/sonidos del idioma Mam.
- **Frases**: botones con frases localizadas.
- **Palabras**: actividad de selección de respuesta con puntuación y bloqueo de intentos.

### 🎮 Minijuegos educativos
- **Memorama**: dinámica de cartas para reforzar memoria y asociación.
- **Match Game**: asociación de imagen ↔ palabra con puntuación y reinicio al terminar.

### 🧭 Cultura
Sección para aprender más sobre elementos culturales, con navegación a módulos dedicados como:
- Música
- Gastronomía
- Tradiciones  
*(Las vistas están preparadas para contenido cultural y UI, ideal para expandirse con información, imágenes y/o audio.)*

### 🔤 Traductor integrado
- Vista `TraductorView` con selección de idioma de origen/destino.
- Traducción desde un servicio `TranslationService` que consume Google Translation API.

---

## 🛠️ Tecnologías utilizadas

- **Swift / SwiftUI** (UI declarativa, navegación y componentes)
- **AVFoundation** (soporte multimedia / audio)
- **Google Cloud Translation API** (traducción en tiempo real vía HTTP)
- **Xcode Project (.xcodeproj)**

---

## 📂 Estructura del proyecto (resumen)

> Este repositorio corresponde a una **versión piloto / prototipo de desarrollo** utilizada para validar la experiencia, navegación, módulos educativos y la integración de traducción.  
> La **versión productiva/final** se mantiene en un repositorio **privado** por motivos de **confidencialidad** y acuerdos con la institución educativa (alcance, contenido y/o materiales licenciados).

```text
ProjectMam/
├─ ProjectMamApp.swift         # Entry point (SwiftUI App)
├─ InicioView.swift            # Pantalla de bienvenida + navegación inicial
├─ BookView.swift              # Vista tipo libro / historia
├─ LeccionView.swift           # Selector de lecciones
├─ AbecedarioView.swift        # Abecedario (navegación por letras)
├─ FrasesView.swift            # Frases básicas localizadas
├─ PalabrasView.swift          # Quiz/actividad de vocabulario (score)
├─ CulturaView.swift           # Módulo cultural con navegación
├─ MusicaView.swift            # Submódulo cultura
├─ GastroView.swift            # Submódulo cultura
├─ TradicionesView.swift       # Submódulo cultura
├─ JuegosView.swift            # Módulo (placeholder/estructura) de juegos
├─ LanguageManager.swift       # Manejo de idioma + carga JSON
├─ LanguageSwitcher.swift      # Componente UI para cambiar idioma
├─ TranslationService.swift    # Cliente HTTP para traducción
└─ Match/, Memorama/           # Minijuegos (vistas + viewmodels)
```

---

## 🧩 Puntos fuertes para un contexto profesional

- Uso de **SwiftUI** con componentes reutilizables y navegación estructurada.
- **Gestión de estado global** para localización mediante `EnvironmentObject`.
- Integración real con un servicio externo (traducción) consumiendo API REST.
- Diseño orientado a escalabilidad: módulos (lecciones, juegos, cultura) fáciles de ampliar.
- Enfoque de producto: app educativa/cultural con múltiples recorridos de usuario.

---

## 🗺️ Roadmap sugerido (si se desea evolucionar)

- Sustituir API key hardcodeada por configuración segura.
- Añadir pruebas unitarias de servicios (traducción) y view models (juegos).
- Completar contenido real de cultura (textos, fuentes, imágenes y audio).
- Accesibilidad (Dynamic Type, VoiceOver labels, contrastes).
- Persistencia de progreso del usuario (lecciones completadas, puntuaciones).

---

## 👨‍💻 Autores

**Samuel Sánchez Guzmán** — iOS (SwiftUI), arquitectura por módulos, localización (i18n) e integración de servicios (API de traducción).  
**Braulio Coutiño Morales** — iOS (SwiftUI), apoyo en contenido/estructura del proyecto y validación funcional del flujo educativo-cultural.  

---

## 📄 Licencia

**© 2024–2026. Todos los derechos reservados.**  
Este repositorio se publica con fines demostrativos/educativos. Para usos, redistribución o implementación en producción, por favor contacta a los autores.
