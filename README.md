# ⚡ MVP by Maktasu - TikTok Live Video Overlay

Una aplicación de escritorio ligera y potente que conecta tus transmisiones de TikTok LIVE con OBS Studio. Permite reproducir videos o animaciones locales (MP4/WebM) con fondo transparente de forma automática cuando tus espectadores interactúan y envían regalos en tu directo.

## ✨ Características Principales

* 🎯 **Respuestas Personalizadas:** Configura videos específicos para regalos exactos (Rosas, Leones, Galaxias) o para usuarios específicos.
* 💰 **Umbral de Monedas:** ¿Quieres un video épico para cualquier donación grande? Establece un mínimo de monedas y la aplicación ignorará el nombre del regalo para activar la alerta general.
* 🛡️ **Filtro Anti-Spam Inteligente:** Detecta cadenas o "combos" de regalos repetidos (con un cooldown de 5 segundos) para no saturar tu pantalla con el mismo video docenas de veces.
* ⏳ **Cola de Reproducción:** Si recibes múltiples donaciones al mismo tiempo, el sistema las organiza en una cola y reproduce los videos uno por uno de forma ordenada.
* ☁️ **Sistema de Cuentas:** Autenticación integrada vía Firebase (Email y Google) con registro de Nicknames únicos.
* 👑 **Modelo Freemium:** Los usuarios gratuitos pueden configurar hasta 10 reglas de video simultáneas. Las cuentas PRO disfrutan de animaciones ilimitadas y sin caducidad.

## 🛠️ Tecnologías Utilizadas

* **Backend:** Python, Flask.
* **Conexión a TikTok:** `TikTokLive` (Librería de Python).
* **Frontend:** HTML5, CSS3, JavaScript puro (UI moderna y reactiva).
* **Base de Datos & Auth:** Firebase Firestore y Firebase Authentication.
* **Distribución:** PyInstaller + PyArmor (Ofuscación y empaquetado en `.exe`).

## 🚀 Instalación y Uso

### 1. Iniciar la Aplicación
1. Descarga y ejecuta el archivo `app.exe`. 
2. No verás ninguna consola de comandos; el programa abrirá automáticamente tu navegador web predeterminado mostrando el Panel de Control.
3. Inicia sesión o crea una cuenta para comenzar a configurar tus reglas.

### 2. Configurar en OBS Studio (⚠️ Requisito Indispensable)
Debido a las estrictas políticas de seguridad de TikTok Live Studio, no es posible pegar enlaces de servidores locales directamente allí. **Es obligatorio utilizar OBS Studio** como puente para generar el fondo transparente.

**¿Ya tienes tu lienzo de OBS configurado en vertical?**
Si aún no lo tienes listo para TikTok, configúralo siguiendo estos pasos:
1. Abre OBS Studio y entra a **Ajustes** (Settings).
2. Dirígete a la pestaña **Video**.
3. En **Resolución de la base (Lienzo)** y **Resolución de salida (Escalada)**, borra lo que haya y escribe manualmente `1080x1920`.
4. Haz clic en Aplicar y Aceptar.

**Vincular la aplicación:**
1. En tu panel de control web, haz clic en el botón **Abrir Pantalla de Overlay (Para OBS)**.
2. Copia la URL de esa nueva pestaña (será `http://127.0.0.1:5000/overlay`).
3. En OBS Studio, ve al panel de *Fuentes*, haz clic en el botón `+` y selecciona **Navegador** (Browser).
4. Pega la URL en la ventana de propiedades.
5. Configura el **Ancho** en `1080` y el **Alto** en `1920`. Asegúrate de colocar esta capa visualmente por encima de tu juego o cámara.

### 3. Enviar la señal a TikTok Live Studio
1. En los controles de OBS (esquina inferior derecha), haz clic en el botón **Iniciar Cámara Virtual**.
2. Abre TikTok Live Studio, agrega una nueva fuente de tipo **Cámara** y selecciona **"OBS Virtual Camera"**.
3. Vuelve a tu panel de control web de *MVP by Maktasu*, ingresa tu `@usuario` de TikTok y presiona **Conectar Transmisión**. ¡Todo listo!

## ⚙️ ¿Cómo funcionan las reglas de prioridad?

El sistema evalúa cada donación en tiempo real y busca el video correcto siguiendo este orden de prioridad (del más específico al más general):

1. **Valor en monedas:** Si el regalo supera la cantidad de monedas establecida y coincide con el usuario (o `@todos`), se reproduce esa alerta (ignorando el nombre específico del regalo).
2. **Coincidencia Exacta:** Nombre de regalo específico + Usuario específico (Ej: *Juan envía una Rosa*).
3. **Regalo para todos:** Nombre de regalo específico + Cualquier usuario (`@todos`).
4. **Usuario VIP:** Cualquier donación (`todos`) + Usuario específico.
5. **Comodín General:** Cualquier donación (`todos`) + Cualquier usuario (`@todos`).

> **💡 Tip de formato:** Utiliza videos en formato `.webm` si deseas que tus animaciones mantengan su fondo transparente original en pantalla.

---
**Desarrollado por [Maktasu](https://www.maktasu.com)** - *Potenciando a los creadores de contenido.*
