# CañaLab

Planta Virtual de Procesos Agroindustriales · biorrefinería de caña de azúcar a escala industrial.
Programa de Ingeniería Agroindustrial, Universidad Surcolombiana.
Docente: Ing. Jaime Daniel Bustos, D.Sc.

Recorrido 3D en primera persona por un ingenio que muele 400 t de caña por hora. La nave occidental tiene el patio y la molienda; al norte están la caldera de bagazo y el turbogenerador; la casa de cocimiento (clarificación, sulfitación, evaporación, tachos, centrífugas, secado y empaque) ocupa el centro, y al oriente están la destilería y el manejo de vinaza. Dos líneas de producto salen de la misma caña: azúcar morena en bolsa de 1 kg y azúcar blanca en bulto de 50 kg, y etanol anhidro carburante a partir de la miel final, con el bagazo convertido en vapor y energía eléctrica.

Doce turnos, calificados contra la norma, la orden del cliente y la eficiencia del proceso:

| Turno | Proceso | Línea | Referencia normativa |
|---|---|---|---|
| 1 | Molienda: preparación e imbibición | Común | Estándar de fábrica |
| 2 | Cogeneración con bagazo | Común | Estándar de fábrica |
| 3 | Clarificación del jugo | Común | Estándar de fábrica |
| 4 | Sulfitación | Azúcar blanca | NA 0009:2002 (SO₂) · Codex Stan 212-1999 (color) |
| 5 | Evaporación de múltiple efecto | Común | Estándar de fábrica |
| 6 | Cocimiento en tachos | Azúcar blanca | Estándar de fábrica |
| 7 | Centrífugas | Morena y blanca | NA 0008:2002 (morena) · Codex Stan 212-1999 (blanca) |
| 8 | Secado y enfriamiento | Azúcar blanca | NA 0009:2002 (humedad) |
| 9 | Empaque 1 kg y 50 kg | Morena y blanca | Resolución 32209 de 2020 (SIC), contenido de preempacados |
| 10 | Fermentación alcohólica | Bioetanol | Estándar de destilería |
| 11 | Destilación y deshidratación | Bioetanol | Resolución 789 de 2016 (etanol anhidro combustible) |
| 12 | Vinaza: concentración y fertirriego | Bioetanol | Plan de manejo de suelos |

Los modelos de proceso son didácticos: reproducen las tendencias y los órdenes de magnitud de un ingenio colombiano, pero no son el balance de una planta específica.

## Archivos

```
index.html                        la aplicación completa (un solo archivo)
manifest.json                     datos para instalarla como aplicación en el PC
sw.js                             funcionamiento sin conexión y actualización automática
icon-192.png, icon-512.png        íconos
registro_canalab_apps_script.gs   backend del registro de uso (va en Google Apps Script, no en GitHub)
```

## Publicar en GitHub Pages (igual que las otras plantas)

1. En GitHub, crea un repositorio nuevo llamado `CanaLab` (público, sin tilde ni eñe para que la dirección sea limpia).
2. **Add file → Upload files**: sube `index.html`, `manifest.json`, `sw.js`, `icon-192.png` e `icon-512.png`.
3. **Settings → Pages → Deploy from a branch → main / (root) → Save**.
4. En uno o dos minutos queda en `https://jaimebustos1982.github.io/CanaLab/`.

En el PC, Chrome o Edge muestran el botón **Instalar** en la barra de direcciones: así queda como aplicación de escritorio, con su ícono, y funciona sin conexión.

**Logo:** la aplicación busca un archivo `logo-usco.png` en el repositorio. Si lo subes junto a los demás archivos, aparece en la barra superior y en la pantalla de ingreso; si no, muestra el distintivo «USCO».

## Activar el registro central (hoja exclusiva de CañaLab)

Cada Lab tiene su propia Google Sheet. No pegues este script en la hoja de NectarLab, LactoLab, CacaoLab ni CaféLab.

1. Crea una Google Sheet nueva llamada **Registro CañaLab**.
2. **Extensiones → Apps Script**. Borra el contenido y pega todo `registro_canalab_apps_script.gs`. Guarda.
3. **Implementar → Nueva implementación → tipo Aplicación web**.
   - Ejecutar como: **Yo**.
   - Quién tiene acceso: **Cualquier usuario**.
4. Autoriza y copia la URL que termina en `/exec`.
5. En `index.html`, busca `const SHEET_WEBAPP_URL="";` y pega la URL entre las comillas.
6. Sube de nuevo `index.html`. Cambia la versión en los dos archivos: `VERSION` en `index.html` (de `2026.10.07-F1` a `-F2`) y `CACHE_NAME` en `sw.js` (igual).

Cada vez que edites el Apps Script: **Implementar → Gestionar implementaciones → editar → Nueva versión** (la URL no cambia).

## Código de acceso docente

`CANA-2026`. Está en `DOCENTE_CODE` (index.html) y en `SECRET` (Apps Script); si cambias uno, cambia el otro. El código viaja dentro del archivo, así que protege de curiosos, no de alguien que lea el código fuente.

## Qué registra

Cada ingreso, cada lote producido y cada cierre de sesión, con: integrantes y códigos, modalidad, grupo, turno, línea de producto, número de intento, estrellas, puntos, predicción y valor real, resultado por categoría (inocuidad y seguridad, norma, cliente, eficiencia), fallas, indicador de eficiencia, tiempo activo en el turno, tiempo activo total y las variables que fijó el equipo. El tiempo activo solo corre con la ventana visible y actividad en los últimos 2 minutos.

El panel docente muestra el resumen por estudiante (12 turnos, 36 estrellas), la dificultad por turno y los últimos lotes, y exporta tres archivos CSV (separador `;`, abren directo en Excel en español). Desde el panel también se cambian los precios unitarios (azúcar, electricidad comprada y vendida, vapor, bagazo, cal, floculante, azufre, etanol y transporte de vinaza) y se pueden habilitar todos los turnos. Los precios mueven el óptimo económico: por ejemplo, si el bagazo se vende más caro que la energía que genera, en el turno 2 conviene quemar menos.

## Para verificar que un cambio llegó

El pie del panel docente muestra la versión (`2026.10.07-F1`). Cámbiala en `VERSION` dentro de `index.html` y en `CACHE_NAME` de `sw.js` cada vez que publiques.
