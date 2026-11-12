# English Lab UK · cuentas, vocabulario y evaluación oral

La edición conserva las 19 secciones originales. Se añadieron:
- Vocabulary separado por niveles A1, A2, B1, B2, C1, C2 (temas de un nivel a la vez)
- Listening: práctica de repetir y hablar con coincidencia de palabras reconocidas, no examen profesional de acento
- Crear cuenta / Iniciar sesión y sincronización opcional con Supabase Auth y RLS

## Publicación en GitHub Pages
Extrae este ZIP. Sube `index.html` y los demás archivos a la raíz de tu repositorio `english-lab-uk`.
Settings → Pages → Deploy from a branch → main / (root).

## Activación de usuarios reales y sincronización entre dispositivos
GitHub Pages no ejecuta bases de datos ni autentica usuarios por sí mismo. Es NECESARIO configurar Supabase una vez:
1. Crea un proyecto en https://supabase.com/dashboard.
2. En Supabase, SQL Editor → New query, pega `supabase_setup.sql` y ejecútalo.
3. En Authentication → Providers, habilita Email. Para correos de confirmación reales, configura las opciones de SMTP y las URL de redirección permitidas en Authentication → URL Configuration. Site URL puede ser tu URL de GitHub Pages.
4. En Project Settings → API Keys, copia SOLO la clave pública publishable (o legacy anon). Nunca utilices `service_role` ni `sb_secret_`.
5. Abre tu English Lab UK en HTTPS. Pulsa «👤 Cuenta» y coloca la Project URL `https://xxxxx.supabase.co` y la publishable/anon key. Hazlo también en los otros dispositivos, ya que la conexión se configura en cada navegador.
6. Crea una cuenta con email y contraseña; confirma el correo si tu proyecto lo exige. Inicia sesión.
7. Para guardar la copia del dispositivo, pulsa «Guardar mi avance en la nube». Para usar un dispositivo nuevo, inicia sesión y pulsa «Recuperar avance de la nube». Confirma antes de reemplazar tus datos. Cuando la sincronización está habilitada, se intenta guardar automáticamente aproximadamente cada 25 segundos.

### Qué se sincroniza
Avances, puntajes, borradores, selección de niveles, frases y dictados almacenados en localStorage (máximo aprox. 2,6 MB por copia). Los MP3 y PDF privados guardados como archivos o IndexedDB NO se sincronizan. Si el navegador no permite almacenamiento, el guardado local no podrá garantizarse.
No se garantiza sincronización en tiempo real ni protección contra escritura simultánea desde varios dispositivos; para ello habría que implementar resolución de conflictos.

### Cómo funciona la nota de Listening
La calificación usa las palabras reconocidas por el navegador en-GB y su orden. No mide la pronunciación acústica. El reconocimiento depende del servicio de voz de Chrome y requiere HTTPS y permiso del micrófono.

### Seguridad
La clave publishable/anon se puede usar en el cliente con Row Level Security. NUNCA uses una clave secreta, ni publiques MP3 privados, PDF de Cambridge o contraseñas en GitHub.
