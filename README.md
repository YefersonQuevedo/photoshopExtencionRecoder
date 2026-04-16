# F_Record 3 — Fork para Photoshop 2020

Extensión CEP para Adobe Photoshop que graba automáticamente el proceso de dibujo y lo exporta como timelapse en video.

> **Fork realizado por [YefersonQuevedo](https://github.com/YefersonQuevedo/photoshopExtencionRecoder)**
> con mejoras de compatibilidad para Photoshop 2020 y nuevas funcionalidades.
>
> Créditos al creador original: **[F_know]([https://space.bilibili.com/390484](https://github-com.translate.goog/F-know/F_Record?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc))** — autor de F_Record 3.

---

## Mejoras de este fork

- ✅ Compatibilidad con **Photoshop 2020** (CEP 9 / Chromium 73 / Node.js 8)
- ✅ Traducción al **español**
- ✅ Duración de **transición configurable** (0.5s / 1s / 2s / 3s / 5s)
- ✅ Velocidad de timelapse configurable: **rápido / original / lento / muy lento** con segundos estimados en tiempo real
- ✅ Fix: el spinner de "cargando" ya no se queda atascado indefinidamente

---

## Requisitos

- Adobe Photoshop 2020 (versión 21.x) o superior
- Windows 10/11

---

## Instalación

### 1 — Copiar la extensión CEP

Copia la carpeta `com.f_know.f_record.cep` a:

```
C:\Users\<tu_usuario>\AppData\Roaming\Adobe\CEP\extensions\
```

> Si la carpeta `extensions` no existe, créala manualmente.

### 2 — Copiar el plugin generator

Copia la carpeta `com.f_know.f_record.generator` a:

```
C:\Program Files\Adobe\Adobe Photoshop 2020\Required\Generator\
```

### 3 — Activar modo desarrollador (evitar error de firma)

Ejecuta en **PowerShell como administrador**:

```powershell
reg add "HKCU\Software\Adobe\CSXS.10" /v PlayerDebugMode /t REG_SZ /d 1 /f
reg add "HKCU\Software\Adobe\CSXS.9" /v PlayerDebugMode /t REG_SZ /d 1 /f
```

### 4 — Abrir Photoshop

Reinicia Photoshop 2020. La extensión aparecerá en:

**Ventana → Extensiones → F_Record 3**

---

## Uso

1. Abre un documento en Photoshop
2. Activa la grabación con el botón **Activado** en el panel
3. Dibuja normalmente — cada pincelada se captura automáticamente
4. Cuando termines, haz clic en **Exportar** y elige:
   - **Relación de aspecto** del video
   - **Duración**: rápido / original / lento / muy lento (con segundos estimados)
5. Selecciona dónde guardar el `.mp4` y confirma

---

## Configuración (pestaña Ajustes)

| Opción | Descripción |
|--------|-------------|
| Carpeta de imágenes | Dónde se guardan las capturas del proceso |
| Resolución | Calidad del video exportado |
| Calidad | Compresión JPEG de las capturas |
| Tiempo inactivo | Pausa el temporizador si no hay actividad |
| Idioma | Chino / Inglés / Español |
| Transición | Duración del fade de entrada/salida (0.5s – 5s) |

---

## Notas técnicas sobre la compatibilidad con PS2020

Photoshop 2020 usa CEP 9 con Chromium 73 y Node.js 8. Las correcciones aplicadas:

- `catch {}` sin parámetro → `catch (_e) {}` (no soportado en Chromium 73)
- Polyfill para `FinalizationRegistry` (añadido en Chrome 84)
- Polyfill para `Object.fromEntries` (añadido en Chrome 73, límite exacto)
- Polyfill para `queueMicrotask` (añadido en Chrome 71)
- `fs.rmSync` → implementación manual recursiva (añadido en Node.js 14)
- Fix en generator: `isGettingImage` siempre se resetea en `finally`

---

## Créditos

| Rol | Persona |
|-----|---------|
| Creador original de F_Record 3 | [F_know](https://space.bilibili.com/390484) |
| Fork PS2020 + nuevas funciones | [YefersonQuevedo](https://github.com/YefersonQuevedo) |
