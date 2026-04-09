# apoyo-financiero-web2-

Landing de Apoyo Financiero publicada en GitHub Pages con:

- Sitio informativo
- Formulario de contacto a WhatsApp
- Registro y login con Supabase Auth
- Guardado de leads en Supabase

## URL publica

https://jose061125.github.io/apoyo-financiero-web2-/

## Configuracion de Supabase

1. Crea un proyecto en Supabase.
2. En SQL Editor, ejecuta el contenido de [supabase-schema.sql](supabase-schema.sql).
3. En Project Settings > API copia:
	- Project URL
	- anon public key
4. Abre [index.html](index.html) y completa:
	- SUPABASE_URL
	- SUPABASE_ANON_KEY
5. Haz commit y push para publicar cambios.

## Flujo funcional

- Registro: crea usuarios reales con Supabase Auth.
- Login: autentica usuarios con email y contrasena.
- Leads: al enviar el formulario de contacto, se guarda un registro en la tabla leads y ademas se abre WhatsApp con mensaje prellenado.
- Referidos: cada usuario autenticado tiene su codigo, enlace y QR para invitar personas con `?ref=CODIGO`.

## Programa de referidos con QR

### Que incluye

- Captura de codigo desde URL (`?ref=...`) y almacenamiento temporal.
- Aplicacion automatica de referido cuando el usuario se registra/inicia sesion.
- Panel "Invita y gana" con:
	- codigo de referido
	- enlace para compartir
	- codigo QR
	- boton para copiar enlace

### Requisito de base de datos

Ejecuta nuevamente [supabase-schema.sql](supabase-schema.sql) para crear:

- `public.profiles`
- `public.referrals`

Estas tablas y politicas RLS son necesarias para que funcione el flujo de referidos.

## Analitica de conversion (opcional)

La landing ya incluye eventos de conversion listos para medir embudo:

- `whatsapp_click`
- `lead_submit_attempt`
- `lead_submit_success`
- `lead_submit_error`
- `register_attempt`
- `register_success`
- `register_error`
- `login_attempt`
- `login_success`
- `login_error`

Para activar Google Analytics 4:

1. Crea una propiedad web en GA4 y copia el Measurement ID (formato `G-XXXXXXXXXX`).
2. Abre [index.html](index.html).
3. Asigna ese valor a la constante `ANALYTICS_GA4_ID`.
4. Publica cambios.

Si `ANALYTICS_GA4_ID` queda vacio, no se envia trafico a GA4 y los eventos solo quedan en `window.dataLayer`.

## Notas

- El anon key de Supabase puede estar en frontend, pero debes usar RLS para proteger tablas.
- Si activas confirmacion por correo en Supabase Auth, el usuario debe confirmar email antes de iniciar sesion.