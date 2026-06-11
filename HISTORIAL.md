# Historial del Prode Mundial 2026

## Resumen de cambios realizados

### 1. Modal de ayuda actualizado
- Se agregó info sobre: Campeón (+10 pts), Goleador (+5 pts), desempate por 3p, PDF descargable, compartir ranking como imagen, fechas separadas por jornada.

### 2. Indicador "🔒 Cerrado" para partidos jugados
- Los partidos con resultado real cargado se muestran con badge "🔒 Cerrado", opacidad reducida y sin inputs.
- El admin sigue viendo inputs para editar resultados reales.

### 3. Lista de participantes
- En la pestaña Ranking se agregó una sección "👥 Participantes (N)".
- Muestra ✅ si ya cargaron predicción, ⏳ si todavía no.
- El admin puede hacer clic en el nombre para editar, y ve un enlace "PDF" para descargar.

### 4. PDF auto-descarga después de guardar
- Al guardar la predicción, el PDF se descarga automáticamente a los 500ms.
- PDF mejorado: incluye Campeón, Goleador, separadores de Fecha, resultados reales y puntajes.
- Fallback a vista de impresión si jsPDF falla.
- Carga dinámica de jsPDF desde 3 CDNs (cdnjs → unpkg → jsdelivr).
- Botón 📄 PDF permanente visible después de guardar.

### 5. Admin: ver/editar predicciones desde el nombre
- El admin puede hacer clic en cualquier nombre de participante (lista o ranking) para ver/editar sus predicciones.
- Al editar, se mantienen los valores existentes si no se modifican.
- Se quitó la sección de predicción (Campeón/Goleador) para el admin en modo general; solo ve los campos "real".

### 6. Fase Eliminatoria (🏆 Eliminatoria)
- Se agregaron 31 partidos de eliminación directa: 32vos → 8vos → 4tos → Semi → Final.
- Los cruces se arman automáticamente según los resultados de grupo de cada usuario.
- Función `calcularTabla()`: calcula posiciones de grupo (puntos, diferencia de gol, goles a favor).
- Función `resolverBracket()`: resuelve todos los enfrentamientos de la llave.
- Nueva pestaña "🏆 Eliminatoria" que se habilita después de guardar grupos.
- Dos guardados separados: primero grupos, después eliminatoria.
- Misma puntuación 3/1/0 para eliminatoria.
- El admin carga resultados reales de eliminatoria desde el mismo panel.
- PDF incluye grupos + eliminatoria.
- Resumen visual en la pestaña de grupos con tabla de eliminatoria.

### 7. Correcciones de bugs
- **`calcularTabla`**: se corrigió bug donde los equipos compartían el mismo objeto de estadísticas.
- **Keys numéricos en objeto literal**: se corrigió error de sintaxis (`32vos`, `8vos`, `4tos` deben ir entre comillas como keys de objeto).

---

## Estructura del proyecto
- `C:\prode\index.html` — App principal (single file, ~1237 líneas)
- `C:\prode\test.html` — Versión demo (precargada con 3 usuarios)
- `C:\prode\generar_excel.py` — Script para generar backup en Excel
- `C:\prode\Prode Mundial 2026.xlsx` — Backup en Excel
- `C:\prode\HISTORIAL.md` — Este archivo

## Datos técnicos
- Firebase: `prode-mundial-2026-8ae43`
- Firestore: documento `prode/datos` con campos `usuarios` (map), `reales` (array), `campeon_real`, `goleador_real`
- Reglas: `allow read, write: if true`
- Hosting: GitHub Pages → `https://hmonzon-prog.github.io/prode-mundial-2026/`
- Admin password: `admin123`

## Partidos
- Fase de grupos: 72 partidos (12 grupos × 6 partidos cada uno)
- Fase eliminatoria: 31 partidos (16 + 8 + 4 + 2 + 1)
- Total: 103 partidos
