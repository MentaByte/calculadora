# 🧮 Calculadora

Calculadora Android/iOS fake (PWA) con menú de personalización oculto. Es una versión simplificada de `calculadora-auth`: **sin sistema de licencias, sin verificación de código en base de datos y sin Supabase**. La app se abre y funciona directo, sin activación ni internet.

## 📋 Estructura del proyecto

```
calculadora/
├── index.html          # Calculadora (skin Android)
├── manifest.json       # Configuración PWA (Android)
├── sw.js                # Service Worker (Android)
├── icon-192.png
├── icon-512.png
└── ios/
    ├── index.html       # Calculadora (skin iOS)
    ├── manifest.json    # Configuración PWA (iOS)
    └── sw.js             # Service Worker (iOS)
```

## 🚀 Cómo funciona

La app carga la calculadora inmediatamente, sin pantalla de activación ni validación de red. Todo el estado (número a forzar, colores, fuente, tamaños) se guarda en `localStorage` del dispositivo.

## 📱 Instalación como PWA

- **Chrome/Edge:** Menú → Instalar app
- **Safari iOS:** Compartir → Agregar a pantalla de inicio
- **Firefox:** Menú → Instalar

## ⚡ Modo offline

El Service Worker cachea los archivos locales (HTML, manifest, iconos) con estrategia cache-first, así que después de la primera carga la app funciona sin conexión.

## 🎨 Menú secreto

Presiona el botón **⚙️** para acceder al menú de configuración:

1. **⭐ Número a forzar** — define qué número mostrará el botón `=` al presionar `-` y luego cualquier dígito.
2. **🎨 Personalización de colores** — botones numéricos, de signos, botón igual, fondo y fuente.
3. **🔤 Fuente** y **📏 Tamaño de fuente** (display y botones).
4. **👁️ Opacidad y tamaño** del botón de configuración y del indicador de dígitos.
5. **📱 Apariencia iPhone** (solo en la versión Android): alterna entre el skin Android y un preset estilo iOS.

Toda la configuración se guarda automáticamente y se restaura al abrir la app. Botón "Restaurar" para volver a los valores por defecto.

## 🔧 Diferencias con `calculadora-auth`

- Sin `auth.js`, sin Supabase, sin `fenix.html` ni pantalla de activación por código.
- Sin `device_id` / `session_token`: no hay ningún dato enviado a un servidor.
- El Service Worker ya no distingue rutas "de validación" — todo se cachea igual (cache-first).
- La calculadora vive directamente en `index.html` (y `ios/index.html`), no dentro de una carpeta `/core/` protegida.

## 🧪 Testing local

```bash
npx serve .
# o
python -m http.server 8000
```

Abre `http://localhost:8000/` (skin Android) o `http://localhost:8000/ios/` (skin iOS).

---

**Listo para usar** 🚀
