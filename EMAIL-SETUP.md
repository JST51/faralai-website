# CONFIGURACIÓN DE EMAILS - Faralai Audit Form

## 🚨 IMPORTANTE: Configuración Actual

El formulario actualmente usa **mailto** que:
- ✅ Funciona inmediatamente sin configuración
- ⚠️ Abre el cliente de email del usuario (Gmail, Outlook, etc.)
- ⚠️ El usuario debe hacer clic en "Enviar" en su cliente de email
- ⚠️ No funciona si el usuario no tiene cliente de email configurado

## ✨ SOLUCIÓN PROFESIONAL: Formspree (Recomendado)

### Paso 1: Crear Cuenta en Formspree
1. Ve a https://formspree.io
2. Regístrate gratis (permite 50 submissions/mes)
3. Crea un nuevo form
4. Copia tu Form ID (algo como: `xpzvgrlq`)

### Paso 2: Modificar el Código

Busca esta línea en `index.html` (línea ~555):

```javascript
const handleSubmit=()=>{
```

Y reemplázala con:

```javascript
const handleSubmit=async(e)=>{
  e?.preventDefault();
  
  try {
    // Enviar a Formspree
    const response = await fetch('https://formspree.io/f/TU_FORM_ID_AQUI', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        name: form.name,
        email: form.email,
        company: form.company,
        industry: form.industry,
        goal: form.goal,
        _subject: `Free Audit Request from ${form.name}`,
        _replyto: form.email
      })
    });
    
    if (response.ok) {
      setSubmitted(true);
      console.log('✅ Email sent successfully!');
    } else {
      alert('Error sending form. Please try again.');
    }
  } catch (error) {
    console.error('Error:', error);
    alert('Error sending form. Please email us directly at info@faralai.com');
  }
};
```

Reemplaza `TU_FORM_ID_AQUI` con tu Form ID de Formspree.

### Paso 3: Listo!
Los emails llegarán automáticamente a info@faralai.com sin que el usuario vea nada.

---

## 🔧 ALTERNATIVA 2: EmailJS

### Paso 1: Crear Cuenta en EmailJS
1. Ve a https://emailjs.com
2. Regístrate gratis
3. Crea un servicio de email
4. Crea una plantilla
5. Copia:
   - Service ID
   - Template ID  
   - Public Key

### Paso 2: Agregar EmailJS Script

Antes de `</head>` en index.html, agrega:

```html
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
<script>
  emailjs.init('TU_PUBLIC_KEY');
</script>
```

### Paso 3: Modificar handleSubmit

```javascript
const handleSubmit=()=>{
  emailjs.send(
    'TU_SERVICE_ID',
    'TU_TEMPLATE_ID',
    {
      from_name: form.name,
      from_email: form.email,
      company: form.company,
      industry: form.industry,
      goal: form.goal,
      to_email: 'info@faralai.com'
    }
  ).then(
    () => {
      setSubmitted(true);
      console.log('✅ Email sent!');
    },
    (error) => {
      console.error('Error:', error);
      alert('Error sending form.');
    }
  );
};
```

---

## 🎯 RECOMENDACIÓN

**Usar Formspree** porque:
- Más fácil de configurar
- No necesitas plantillas
- Plan gratuito generoso (50/mes)
- Menos código
- Más confiable

## 📧 Testing

Para testear que funciona:
1. Llena el formulario
2. Haz clic en "Request Free Audit"
3. Revisa tu email en info@faralai.com
4. Deberías recibir el email con toda la información

## ⚠️ Versión Actual (Mailto)

Si no configuras Formspree/EmailJS:
- El formulario abre el cliente de email del usuario
- Funciona, pero es menos profesional
- Algunos usuarios pueden no tener email configurado
- El usuario ve que se abre su Gmail/Outlook

---

¿Necesitas ayuda configurando Formspree? ¡Avísame! 🚀
