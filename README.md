# Generador de Presupuestos - BOTCRAFmaker

Este es el repositorio oficial para el wizard profesional de presupuestos de **BOTCRAFmaker**. Una solución "todo en uno" para autónomos que integra frontend web, automatización con n8n y base de datos en Airtable.

## 🚀 Características
- **Wizard de 3 Pasos:** Cliente -> Líneas -> Confirmación.
- **Cálculos Automáticos:** Totales y subtotales en tiempo real.
- **Marca Corporativa:** Logo y datos fiscales de Pedro Juan Muñoz Esteve (NIF: 334682).
- **Integración con n8n:** Envío de datos vía Webhook para generación de PDF y registro en Airtable.

## 🛠 Configuración Técnica

### 1. Webhook de n8n
Para que el formulario funcione, debes editar el archivo `index.html` y localizar la variable `WEBHOOK_URL` en la sección de scripts:

```javascript
// Localiza esta línea y reemplaza la URL
const WEBHOOK_URL = 'TU_URL_DE_N8N_AQUI';
```

### 2. Estructura de Datos (JSON)
El wizard envía un objeto JSON con la siguiente estructura al webhook:

```json
{
  "client": "Nombre del Cliente",
  "cif": "NIF del Cliente",
  "address": "Dirección",
  "email": "email@cliente.com",
  "date": "2024-04-13",
  "items": [
    {
      "description": "Concepto 1",
      "qty": "1",
      "price": "100"
    }
  ],
  "total": "100.00 €"
}
```

### 3. Integración con Airtable
En n8n, configura un nodo de Airtable para insertar los datos recibidos. Se recomienda tener dos tablas:
1. **Presupuestos:** Datos maestros (Cliente, Fecha, Total).
2. **Líneas de Presupuesto:** Detalle de cada item vinculado al ID del presupuesto.

## 📦 Despliegue
Este proyecto está optimizado para ser desplegado en **Netlify** o **Vercel** directamente desde GitHub.

---
© 2024 BOTCRAFmaker - Pedro Juan Muñoz Esteve.
