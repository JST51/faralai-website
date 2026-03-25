# 🎯 TRACKING SETUP - Faralai Website

## ✅ LO QUE YA ESTÁ FUNCIONANDO

1. **✅ Formspree Conectado**
   - Endpoint: https://formspree.io/f/xreydpzb
   - Los emails del formulario llegan a: info@faralai.com
   - Estado: FUNCIONANDO ✨

## ⚙️ LO QUE NECESITAS CONFIGURAR

### 1️⃣ GOOGLE ANALYTICS 4

Paso 1: Crear cuenta GA4
1. Ve a: https://analytics.google.com
2. Crea una propiedad nueva
3. Copia tu Measurement ID (formato: G-XXXXXXXXXX)

Paso 2: Agregar el ID al sitio
En index.html, busca la línea 32 y reemplaza:
- G-XXXXXXXXXX con tu Measurement ID real (en 2 lugares)

Eventos trackeados:
- PageView (carga de página)
- Click en "Get Free Audit"
- Click en "View Pricing"  
- Form submission (generate_lead)

### 2️⃣ FACEBOOK PIXEL

Paso 1: Crear Pixel
1. Ve a: Facebook Events Manager
2. Crea un nuevo Pixel
3. Copia tu Pixel ID (números)

Paso 2: Agregar el ID
En index.html, busca la línea 45 y reemplaza:
- YOUR_PIXEL_ID con tu Pixel ID real (en 2 lugares)

Eventos trackeados:
- PageView (carga de página)
- ViewContent (click en CTA)
- Lead (formulario enviado)

## 🧪 TEST DEL FORMULARIO

1. Abre la web
2. Llena el formulario
3. Click en "Request Free Audit"
4. Debe llegar email a info@faralai.com ✅

## ⚠️ NO OLVIDES

- Reemplazar G-XXXXXXXXXX
- Reemplazar YOUR_PIXEL_ID

¡Listo! 🚀
