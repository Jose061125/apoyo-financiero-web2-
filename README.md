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

## Notas

- El anon key de Supabase puede estar en frontend, pero debes usar RLS para proteger tablas.
- Si activas confirmacion por correo en Supabase Auth, el usuario debe confirmar email antes de iniciar sesion.