# Landing · Calcula tu tarifa Trainingym

Landing pública con formulario HubSpot. Punto de entrada al wizard de tarifas.

> 🌐 Web standalone con identidad de marca Trainingym, formulario HubSpot embebido y redirección al wizard tras el envío.

---

## 🎯 Cómo funciona el flujo completo

```
┌──────────────────────┐    Submit    ┌──────────────────────┐
│   ESTA LANDING       │ ───────────> │   WIZARD TARIFAS     │
│   con formulario     │  redirect    │   (proyecto aparte)  │
│   HubSpot embebido   │  con datos   │                      │
│                      │   por URL    │  - Lee URL params    │
│  - hero atractivo    │              │  - Personaliza       │
│  - benefits          │              │  - Pre-configura     │
│  - form HubSpot      │              │  - Genera PNG        │
└──────────────────────┘              └──────────────────────┘
```

El usuario llega a esta landing, rellena el form de HubSpot, y al enviarlo HubSpot lo **redirige al wizard** pasándole los datos por URL.

---

## ⚙️ Cómo configurar la redirección en HubSpot

En tu **formulario de HubSpot** (`bc613e7c-f106-4b5c-8126-649ccc7b9e1b`):

1. Ve a **Forms → tu formulario → Settings → What should happen after a visitor submits this form?**
2. Selecciona **Redirect to another page**
3. Pega la URL del wizard con los tokens de HubSpot:

```
https://tuusuario.github.io/wizard-tarifas-trainingym/?firstname={{contact.firstname}}&lastname={{contact.lastname}}&company={{contact.company}}&modelo={{contact.modelo_de_negocio}}&email={{contact.email}}
```

HubSpot reemplaza `{{contact.X}}` por los valores reales del lead.

---

## 🧱 Estructura de la landing

### Hero (cabecera oscura)
- Logo Trainingym arriba a la izquierda
- Link a trainingym.com a la derecha
- Eyebrow naranja "CONFIGURADOR DE TARIFAS"
- Título principal con palabra "personalizada" destacada en naranja
- Subtítulo explicativo
- 3 píldoras: "Sin compromiso", "100% personalizado", "Descarga tu resumen"

### Sección principal (2 columnas)

**Columna izquierda — Beneficios** (4 puntos):
- 🧮 Configurador interactivo
- 💰 Tarifas mensual/anual −20%
- 📋 Resumen descargable
- 🚧 Hardware control de accesos

**Trust bar** con métricas oficiales Trainingym: 1.200+ negocios · 23 países · 18M+ usuarios

**Columna derecha — Card del formulario**:
- Título "Cuéntanos un poco sobre ti"
- Form HubSpot con estilos brand
- Spinner mientras carga
- Fallback si no carga tras 6s

### Footer
Brand line + enlace a trainingym.com

---

## 🎨 Identidad de marca aplicada

Según [trainingym.com/brand](https://trainingym.com/brand):

| Elemento | Aplicación |
|---|---|
| **Naranja** `#ED6845` | Acentos, CTA, eyebrows |
| **Azul petróleo** `#293138` | Hero background |
| **Negro grafito** `#1D1D1B` | Títulos |
| **Tipografía** | Host Grotesk (Google Fonts) |
| **Logo blanco oficial** | En el topbar del hero |
| **Tono** | Cercano, decidido, "negocio fitness" |

---

## 🚀 Cómo desplegar a GitHub Pages

1. Crea repo público nuevo: [github.com/new](https://github.com/new) → `landing-trainingym-tarifas`
2. Sube el `index.html` y el `README.md` (sin la carpeta contenedora)
3. **Settings → Pages**: Source `Deploy from a branch` → Branch `main` `/` (root) → **Save**
4. Espera 1–2 min → tu URL pública estará lista
5. Comparte esa URL en campañas, ads, web, redes, etc.

---

## 🐛 Problemas comunes

**El formulario no carga**
Comprueba conexión a internet. Si tras 6s no aparece, se muestra automáticamente un fallback con mensaje de error.

**Aparece "el dominio de la clave de reCAPTCHA no es válido"**
Pasa cuando el dominio donde se sirve la web no está en la lista blanca del HubSpot. El error queda oculto visualmente pero puede aparecer en consola. Para solucionarlo de raíz:
- Pedir al admin de HubSpot que añada el nuevo dominio a la lista blanca de reCAPTCHA
- O deshabilitar reCAPTCHA en este formulario concreto

**El usuario no es redirigido al wizard al enviar**
Comprueba que la redirección esté bien configurada en HubSpot (Forms → Settings → Redirect to another page) y que la URL contenga los tokens `{{contact.X}}` correctos.

---

## 📦 Stack técnico

- HTML/CSS/JS vanilla — sin frameworks
- Tipografía: Host Grotesk (Google Fonts)
- Form: HubSpot Forms Embed v2
- Sin build, sin dependencias

Todo en un solo archivo `index.html`.

---

*Trainingym · La tecnología que hace crecer tu negocio fitness · [trainingym.com](https://trainingym.com)*
