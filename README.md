# Pagos App

Panel personal para administrar tarjetas, compras pasadas a cuotas, pagos parciales e historial mensual en soles y dólares.

## Estado actual

- La app se puede publicar con GitHub Pages.
- Sin Supabase funciona como demo y guarda los datos solo en el navegador.
- Con Supabase, cada usuario inicia sesión y su panel se guarda en la nube.
- La app mantiene una copia local como respaldo rápido.

## Conectar Supabase

1. Crea un proyecto gratuito en Supabase.
2. En Supabase abre **SQL Editor**, pega el contenido de `supabase/schema.sql` y ejecútalo.
3. Abre **Project Settings > API**.
4. Copia la URL del proyecto y la clave pública `anon` o `publishable`.
5. Reemplaza los dos valores de `config.js`.
6. En **Authentication > URL Configuration**, agrega la dirección pública de GitHub Pages en **Site URL** y **Redirect URLs**.

Nunca coloques la clave `service_role` en este proyecto. La clave pública puede usarse en el navegador porque la tabla está protegida con políticas que separan los datos por usuario.

## Publicar en GitHub

1. Crea un repositorio público llamado `pagos-app`.
2. Sube estos archivos a la rama `main`.
3. Abre **Settings > Pages** y selecciona **GitHub Actions** como fuente.
4. Espera a que termine la acción **Publicar Pagos App**.
5. Comparte la dirección que aparecerá en la sección **Deployments** del repositorio.

## Archivos principales

- `index.html`: aplicación que abre GitHub Pages.
- `config.js`: conexión pública con Supabase.
- `supabase/schema.sql`: tabla y permisos privados por usuario.
- `.github/workflows/pages.yml`: publicación automática después de cada cambio.
- `outputs/dashboard-pagos.html`: archivo de trabajo local.

## Prueba con usuarios

Cada persona debe usar un correo distinto. Si la confirmación de correo está activada en Supabase, debe confirmar su cuenta antes de iniciar sesión. Los cambios de tarjetas, préstamos e historial se sincronizan automáticamente.
