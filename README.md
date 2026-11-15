# Recepción de Vehículos — Automotriz Salvador Morales

App web para recibir vehículos en el taller desde cualquier celular. Todas las órdenes se guardan en una sola base de datos (Firebase) y se ven en vivo en todos los teléfonos.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | La app completa. No hace falta tocarlo. |
| `firebase-config.js` | Aquí van los datos de tu proyecto de Firebase (paso 1). |
| `firestore.rules` | Las reglas de seguridad que se copian en Firebase (paso 3). |

## Paso 1 — Crear el proyecto en Firebase (gratis)

1. Entra a https://console.firebase.google.com con tu cuenta de Google.
2. **Crear un proyecto** → nombre: `recepcion-taller` → puedes desactivar Google Analytics → **Crear proyecto**.
3. En la página del proyecto, toca el ícono **`</>` (Web)** para agregar una app web. Nombre: `recepcion` → **Registrar app** (no marques Hosting).
4. Te muestra un bloque `const firebaseConfig = { apiKey: ..., authDomain: ..., ... }`. Copia esos valores en `firebase-config.js`, cada uno en su lugar.

## Paso 2 — Activar el inicio de sesión y crear los usuarios

1. Menú izquierdo: **Compilación > Authentication > Comenzar**.
2. En **Método de acceso**, activa **Correo electrónico/contraseña** y guarda.
3. En la pestaña **Usuarios > Agregar usuario**, crea uno para cada persona que va a recibir vehículos (correo y contraseña). Tú, David y los mecánicos.
4. En **Configuración > Dominios autorizados > Agregar dominio**, agrega `efuentess.github.io`.

## Paso 3 — Crear la base de datos

1. Menú izquierdo: **Compilación > Firestore Database > Crear base de datos**.
2. Ubicación: la que sugiera (por ejemplo `nam5 (us-central)`) → **Comenzar en modo de producción** → Crear.
3. Ve a la pestaña **Reglas**, borra lo que hay, pega el contenido de `firestore.rules` y toca **Publicar**.

Las fotos se guardan comprimidas dentro de la misma base, así que no necesitas activar Storage ni poner tarjeta.

## Paso 4 — Subir a GitHub y publicar

1. En https://github.com/new crea el repositorio `recepcion-vehiculos`, **Public**.
2. En el repositorio: **Add file > Upload files**, arrastra `index.html`, `firebase-config.js` y `README.md` → **Commit changes**.
3. **Settings > Pages** → en *Branch* elige `main` y carpeta `/ (root)` → **Save**.
4. En uno o dos minutos la app queda en: **https://efuentess.github.io/recepcion-vehiculos/**

Abre ese link en cada celular, entra con el usuario que le creaste a esa persona y, si quieres, usa "Agregar a la pantalla de inicio" para tenerla como app.

## Uso diario

- **Recibir**: llena la orden (placa, cliente, inventario, daños en el diagrama, fotos y firma) → *Guardar* o *Guardar y descargar PDF*.
- **En taller**: cambia el estado de cada vehículo, avisa por WhatsApp y marca la entrega.
- **Historial**: busca por placa o cliente y exporta a Excel.
- **Ajustes**: datos del taller y condiciones que salen en el PDF.

## Límites del plan gratuito de Firebase (Spark)

50,000 lecturas y 20,000 escrituras por día, y 1 GB de datos. Para un taller sobra; cada foto ocupa unos 100–300 KB, así que caben varios miles de fotos.
