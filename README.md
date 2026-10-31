# CRM y Sistema de Gestión con Google Workspace

Desarrollé un sistema de administración y gestión para una empresa, con el objetivo de centralizar la información y facilitar el trabajo con socios, grupos familiares, pagos, cobradores y reportes.

Mi participación abarcó el diseño de las dos aplicaciones, los formularios, las validaciones, las automatizaciones y las reglas de negocio que las conectan.

**Tecnologías:** Google Sheets, Google Apps Script, HTML, CSS y JavaScript.

## Cómo funciona

| Aplicación | Funcionalidades principales |
| --- | --- |
| **CRM V2** | Alta, modificación y baja de miembros; titulares y grupos familiares; cobradores; tarifas y cuotas; registro, edición y consulta de pagos mediante formularios y validaciones. |
| **Sistema de Gestión** | Consulta General, Consulta de Pagos, Reporte de Cobradores y Reporte de Aumentos, con información de miembros, titulares, pagos y vigencias. |

El CRM administra la información; el Sistema de Gestión consulta esa base mediante Apps Script y genera reportes. La lógica distingue la **cuota calculada** del importe acordado en **Pago Real**. El cambio de titular se realiza mediante el proceso de baja.

## Acceder al proyecto

Las plantillas contienen **datos y tarifas ficticios** y se pueden consultar en modo lectura. Para usar formularios y guardar cambios, creá tus propias copias.

| Aplicación | Consultar | Crear una copia |
| --- | --- | --- |
| **CRM V2** | [Abrir CRM](https://docs.google.com/spreadsheets/d/1F__XB8oZw_CCHPEOkzQgvsAYqut64WGEmB50mKfBSIw/edit) | [Copiar CRM](https://docs.google.com/spreadsheets/d/1F__XB8oZw_CCHPEOkzQgvsAYqut64WGEmB50mKfBSIw/copy) |
| **Sistema de Gestión** | [Abrir Sistema de Gestión](https://docs.google.com/spreadsheets/d/1jQ8q4ZbD2ItUjm_N0BNcDb2xa-xHJa5c0Cwhx8fFSqM/edit) | [Copiar Sistema](https://docs.google.com/spreadsheets/d/1jQ8q4ZbD2ItUjm_N0BNcDb2xa-xHJa5c0Cwhx8fFSqM/copy) |

**Cada copia incluye su Apps Script y los formularios vinculados.** No necesitás descargar código, importar CSV ni instalar archivos por separado.

## Conectar tus copias

1. Creá una copia de **cada planilla** con los enlaces anteriores o desde **Archivo → Crear una copia**. Para copiar y ejecutar el sistema necesitás iniciar sesión en Google.
2. Obtené los IDs de las dos copias: son el texto entre `/d/` y `/edit` en sus URLs. Ejemplo:

   ```text
   https://docs.google.com/spreadsheets/d/ID_DE_TU_COPIA_CRM/edit
   ```

   En ese ejemplo, copiá `ID_DE_TU_COPIA_CRM`.

3. En cada copia, abrí **Extensiones → Apps Script** y reemplazá únicamente los valores entre comillas correspondientes:

   | Proyecto | Archivo | Variable | Valor |
   | --- | --- | --- | --- |
   | Tu CRM | `demoSeguridad.gs` | `DEMO_WORKBOOK_ID` | ID de **tu copia del CRM** |
   | Tu Sistema | `config.gs` | `CONFIG_REPORTES.SPREADSHEET_BASE_ID` | ID de **tu copia del CRM** |
   | Tu Sistema | `demoSeguridad.gs` | `DEMO_BASE_ID` | El mismo ID de **tu copia del CRM** |
   | Tu Sistema | `demoSeguridad.gs` | `DEMO_WORKBOOK_ID` | ID de **tu copia del Sistema** |

   Por ejemplo, la propiedad en `config.gs` del Sistema debe quedar:

   ```javascript
   SPREADSHEET_BASE_ID: "ID_DE_TU_COPIA_CRM",
   ```

   Conservá el resto del archivo. Los controles de aislamiento requieren actualizar **las cuatro referencias**, no solo el ID de la base.

4. Guardá, volvé a abrir ambas planillas y autorizá los permisos de Google cuando una operación los solicite. Usá los menús **Sistema** en el CRM y **Reportes CRM** en el Sistema de Gestión.

Si aparece «Operación bloqueada», revisá el ID propio. Si aparece «referencia de datos no permitida», comprobá que los dos IDs del CRM en el Sistema coincidan. Vinculá siempre tus copias personales, usando sus nuevos IDs.

Para una primera consulta, buscá `DEMO-002`. Los pagos de ejemplo corresponden a septiembre y octubre de 2026; edades, vigencias y aumentos pueden variar con la fecha actual.

## Sobre la demostración

La publicación del código adaptado está autorizada. Las plantillas excluyen los datos privados del cliente y las referencias a sus planillas originales. El código completo puede consultarse desde el Apps Script de cada plantilla.

Las pruebas locales fueron satisfactorias. La validación funcional completa dentro de Google quedó pendiente por limitaciones de acceso a las herramientas; no se presenta como realizada.

**Desarrollado por [Santiago Morandi](https://github.com/MorandiSantiago).**
