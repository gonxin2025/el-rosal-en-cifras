# El Rosal en Cifras – Portal de información estadística

**Código:** ER-PTIC-SW-GIE-001 · **Versión:** 0.5 (borrador) · **Entidad:** Alcaldía Municipal de El Rosal, Cundinamarca
**Coordina:** Secretaría de Planeación · **Administra:** Jefatura de Prensa y TIC

> Entorno de prueba alojado temporalmente en una cuenta personal del contratista de apoyo TIC.
> El código, los datos y los documentos son de la Alcaldía de El Rosal. Transferencia prevista a la cuenta institucional: [PENDIENTE: fecha].

## Contenido
| Archivo | Qué es |
|---|---|
| `index.html` | El portal completo (una sola página, sin compilación). |
| `datos.json` | Corte de datos publicado (indicadores, documentos, fuentes, plan de mejora, instancias). |
| `docs/` | Versiones PDF de consulta de los documentos de acceso público, nombradas con su código del índice maestro. |
| `vercel.json` | Encabezados de seguridad y caché para Vercel. |

## Publicar en Vercel
1. Subir esta carpeta a un repositorio de GitHub.
2. En Vercel: *Add New → Project → Import* el repositorio.
3. Framework preset: **Other**. Build command: vacío. Output directory: `.` (raíz).
4. *Deploy*. Cada cambio que se suba a GitHub se publica solo.

## Migrar al servidor de la Alcaldía o a un subdominio .gov.co
Es un sitio estático: no necesita base de datos ni lenguaje de servidor.
- **Opción A – servidor propio:** copiar `index.html`, `datos.json` y `docs/` a la carpeta raíz del subdominio (Apache, Nginx, IIS o cPanel) y activar HTTPS. `vercel.json` se ignora.
- **Opción B – seguir en Vercel con dominio institucional:** en Vercel, *Settings → Domains* agregar `estadisticas.elrosal-cundinamarca.gov.co` [PENDIENTE: confirmar nombre] y crear en el DNS de la Alcaldía el registro CNAME que Vercel indique.

Todos los enlaces son relativos, así que el portal funciona igual en cualquier dominio.

## Actualizar los datos
1. Planeación valida en el portal de trabajo (pestaña *Revisión*) y pulsa *Exportar datos para el subdominio*.
2. Reemplazar `datos.json` en este repositorio (o en el servidor). No hay que tocar `index.html`.
3. Frecuencia: trimestral, después de cada sesión de la Mesa Técnica.

## Reglas de publicación
- Solo documentos de acceso **Pública** y mediciones con estado **Publicado**.
- Nada clasificado o reservado (matriz de riesgos, vulnerabilidades, MSPI, inventario de equipos). El `.gitignore` los bloquea.
- Sin datos personales: el directorio publica solo cargo y correo institucional.

## Ver en el computador
```
python -m http.server 8000
```
y abrir http://localhost:8000 (con doble clic no carga `datos.json`).
