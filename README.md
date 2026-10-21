# ⚡ MVP by Maktasu - TikTok Live Video Overlay

Una aplicación de escritorio ligera y potente que conecta tus transmisiones de TikTok LIVE con OBS Studio. Permite reproducir videos o animaciones locales (MP4/WebM) con fondo transparente de forma automática cuando tus espectadores interactúan y envían regalos en tu directo.

## ✨ Características Principales

* 🎯 **Respuestas Personalizadas:** Configura videos específicos para regalos exactos (Rosas, Leones, Galaxias) o para usuarios específicos.
* 💰 **Umbral de Monedas:** ¿Quieres un video épico para cualquier donación grande? Establece un mínimo de monedas y la aplicación ignorará el nombre del regalo para activar la alerta general.
* 🛡️ **Filtro Anti-Spam Inteligente:** Detecta cadenas o "combos" de regalos repetidos (con un cooldown de 5 segundos) para no saturar tu pantalla con el mismo video docenas de veces.
* ⏳ **Cola de Reproducción:** Si recibes múltiples donaciones al mismo tiempo, el sistema las organiza en una cola y reproduce los videos uno por uno de forma ordenada.
* ☁️ **Sistema de Cuentas:** Autenticación integrada vía Firebase (Email y Google) con registro de Nicknames únicos.
* 👑 **Modelo Freemium:** Los usuarios gratuitos pueden configurar hasta 10 reglas de video simultáneas. Las cuentas PRO disfrutan de animaciones ilimitadas.
* 🎥 **Integración Nativa con OBS:** Funciona a través de un servidor local HTTP. Solo necesitas agregar una *Fuente de Navegador* en OBS para tener alertas fluidas y con fondo transparente.

## 🛠️ Tecnologías Utilizadas

* **Backend:** Python, Flask.
* **Conexión a TikTok:** `TikTokLive` (Librería de Python).
* **Frontend:** HTML5, CSS3, JavaScript puro (UI moderna y reactiva).
* **Base de Datos & Auth:** Firebase Firestore y Firebase Authentication.
* **Distribución:** PyInstaller + PyArmor (Ofuscación y empaquetado en `.exe`).

## 🚀 Instalación y Uso

### 1. Iniciar la Aplicación
1. Descarga y ejecuta el archivo `app.exe`. 
2. No verás ninguna consola molesta; el programa abrirá automáticamente tu navegador web predeterminado mostrando el Panel de Control.
3. Inicia sesión o crea una cuenta para comenzar a agregar tus reglas.

### 2. Configurar en OBS Studio
1. En tu panel de control web, haz clic en el botón **Abrir Pantalla de Overlay**.
2. Copia la URL de esa nueva pestaña (normalmente `http://127.0.0.1:5000/overlay`).
3. En OBS Studio, crea una nueva **Fuente de Navegador** (Browser Source).
4. Pega la URL, ajusta el ancho y alto según el tamaño de tus videos, y asegúrate de colocar esta capa por encima de tu juego o cámara.

### 3. Conectar a TikTok
1. En el panel de control, ingresa el `@usuario` de la cuenta de TikTok que está transmitiendo en vivo.
2. Haz clic en **Conectar Transmisión**. El indicador cambiará a verde indicando que el sistema está escuchando las donaciones en tiempo real.

## ⚙️ ¿Cómo funcionan las reglas de prioridad?

El sistema evalúa cada donación en tiempo real y busca el video correcto siguiendo este orden de prioridad (del más específico al más general):

1. **Valor en monedas:** Si el regalo supera la cantidad de monedas establecida y coincide con el usuario (o `@todos`), se reproduce esa alerta.
2. **Coincidencia Exacta:** Regalo específico + Usuario específico (Ej: *Juan envía una Rosa*).
3. **Regalo para todos:** Regalo específico + Cualquier usuario (`@todos`).
4. **Usuario VIP:** Cualquier regalo (`todos`) + Usuario específico.
5. **Comodín General:** Cualquier regalo (`todos`) + Cualquier usuario (`@todos`).

> **💡 Tip de formato:** Utiliza videos en formato `.webm` si deseas que tus animaciones mantengan el fondo transparente en pantalla.

---
**Desarrollado por [Maktasu](https://www.maktasu.com)** - *Potenciando a los creadores de contenido.*
