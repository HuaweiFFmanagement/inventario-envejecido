# Seguimiento Promotoría — Inventario Envejecido

Herramienta web para que cada promotor consulte, desde el celular, las referencias
que debe mover en su punto de venta (por antigüedad y nivel de alerta).

## Estructura del repositorio

```
index.html          → la aplicación (promotor + panel de administrador)
data/inventario.json → el inventario publicado actualmente (lo que ve el equipo)
```

## 1. Publicar el sitio en GitHub Pages

1. Crea un repositorio nuevo (puede ser público o privado si tu plan de GitHub lo permite)
   y sube estos dos archivos manteniendo la carpeta `data/`.
2. Ve a **Settings → Pages**.
3. En "Build and deployment" elige **Deploy from a branch**, rama `main`, carpeta `/ (root)`.
4. Guarda. En 1–2 minutos GitHub te da el link público, algo como:
   `https://<tu-usuario>.github.io/<nombre-del-repo>/`
5. Comparte ese link con el equipo — no necesitan hacer nada más, ya verán el
   inventario que está en `data/inventario.json`.

## 2. Actualizar el inventario cada semana

La app **no guarda datos por sí sola** una vez publicada en GitHub Pages (es un
sitio estático). Cada semana debes:

1. Abrir el sitio publicado → **Actualizar inventario** → código `2026`.
2. Subir el `.xlsx` de esa semana (debe tener la hoja llamada **BASE**, con las
   mismas columnas de siempre).
3. Revisar el resumen (total de referencias, tiendas, críticos) y la fecha de corte.
4. Tocar **"Generar y descargar inventario.json"** — esto descarga el archivo a tu celular/PC.
5. En GitHub, entrar a la carpeta `data/`, subir el archivo descargado y **reemplazar**
   el `inventario.json` existente (mismo nombre), luego confirmar el cambio ("Commit changes").
6. En 1–2 minutos el equipo verá la información nueva al abrir el mismo link de siempre.

No hace falta tocar `index.html` para actualizar datos — solo `data/inventario.json`.

## Notas

- El código de acceso al panel de administrador (`2026`) es solo un filtro simple para
  evitar que alguien entre por error; no es una contraseña real, cualquiera que vea el
  código fuente puede verlo. Si necesitas algo más seguro, hay que agregar autenticación real.
- El archivo `data/inventario.json` queda visible para cualquiera con el link del repo
  (aunque el repo sea público). No incluye información distinta a la que ya está en el
  reporte semanal.
- Si abres `index.html` haciendo doble clic desde tu computador (sin publicarlo), la app
  no podrá leer `data/inventario.json` — necesita estar servida por http(s), por eso debe
  abrirse siempre desde el link de GitHub Pages.
