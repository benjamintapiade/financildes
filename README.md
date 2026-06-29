# Financildes — Paso 1 (MVP local)

App de gestión financiera personal, instalable como PWA en tu Samsung.
Offline-first: los datos viven en tu teléfono (localStorage). Estética Obsidian
(oscuro, escala de grises, minimalista).

## Qué incluye este Paso 1
- Registrar **gastos** e **ingresos** con categoría, tarjeta, fecha y nota (todo editable).
- **Categorías** de gasto e ingreso totalmente personalizables (nombre, ícono de línea, tono de gris). Se guardan localmente.
- **Tarjetas** con saldo propio, tipo **débito** (no baja de $0) o **crédito** (permite negativo).
  Saldo inicial editable + acción **“Ajustar saldo”**.
- **Transferencias** entre tarjetas.
- **Gráfico de dona** de gastos por categoría + leyenda con %.
- **Filtros por periodo**: día / semana / mes / año / todo.
- **Balance doble**: Disponible y Patrimonio (por ahora iguales; las deudas del Paso 2 separarán los números).
- **Lista de movimientos** agrupada por día, editable y eliminable.

> Aún NO incluye (vienen en pasos siguientes): gestión de deudas con personas (Paso 2),
> sincronización con Google Sheets (Paso 3), presupuestos y recurrentes (Paso 4).
> El modelo de datos ya está preparado para todo eso, así que no habrá que rehacer nada.

## Cómo desplegarlo en GitHub Pages (HTTPS gratis)

1. Crea un repositorio nuevo en GitHub, por ejemplo `financildes`.
2. Sube **todos** estos archivos a la raíz del repo (no dentro de una subcarpeta):
   `index.html`, `manifest.json`, `service-worker.js`,
   `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `favicon.png`.
3. En el repo: **Settings → Pages**.
4. En “Build and deployment”, Source: **Deploy from a branch**.
   Branch: `main` (o `master`), carpeta: `/ (root)`. Guarda.
5. Espera ~1 minuto. GitHub te dará una URL tipo
   `https://TU-USUARIO.github.io/financildes/`.
6. Abre esa URL en **Chrome** en tu Samsung.
7. Menú (⋮) → **Agregar a pantalla de inicio** / **Instalar app**.
   Quedará con su ícono y se abrirá a pantalla completa, funcionando offline.

## Notas técnicas
- Los datos se guardan en `localStorage` del navegador donde la instales.
  Es local a ese dispositivo/navegador (la sincronización entre los hasta 4
  usuarios llegará con Google Sheets en el Paso 3).
- Si actualizas los archivos en GitHub, **sube el número de versión** en
  `service-worker.js` (`const CACHE = 'financildes-v2'`, etc.) para forzar que
  el teléfono tome la versión nueva.
- No requiere cuenta, login ni conexión para funcionar.

## Probarlo antes de subir
Como las PWA necesitan HTTPS para instalarse, no basta con abrir el archivo
suelto. Para probar en tu computador puedes levantar un servidor local:
```
python3 -m http.server 8000
```
y abrir `http://localhost:8000`. (La instalación como app igual conviene
probarla ya en el teléfono vía la URL de GitHub Pages.)
