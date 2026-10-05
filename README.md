# 🤖 Asistente Virtual por Telegram para Gestión de Trabajos y Facturas (Automatización con Make.com)

Un flujo de trabajo automatizado (blueprint) construido en [Make](https://www.make.com) que utiliza un bot de Telegram como interfaz para gestionar partes de trabajo de electricidad y procesar facturas automáticamente usando Inteligencia Artificial (OpenAI). 

Ideal para profesionales independientes, técnicos y pequeñas empresas que desean registrar sus trabajos y gastos en movimiento, enviando simplemente un audio o una foto por Telegram.

## 🌟 Características Principales

Esta automatización tiene dos flujos principales (Rutas):

1. **🎙️ Procesamiento de Partes de Trabajo (Notas de Voz):**
   - Recibe una nota de voz a través de Telegram detallando un trabajo realizado.
   - Utiliza **Whisper (OpenAI)** para transcribir el audio a texto.
   - Utiliza **GPT-4o-mini** para extraer datos estructurados: *Fecha del trabajo, Cliente/Obra, Horas trabajadas, Materiales utilizados y Observaciones*.
   - Guarda automáticamente estos datos en una nueva fila de **Google Sheets**.

2. **📸 Análisis de Facturas y Tickets (Fotos):**
   - Recibe una foto de una factura o ticket de compra de materiales por Telegram.
   - Sube y respalda la imagen en **Google Drive**.
   - Utiliza **GPT-4o (Visión)** para analizar la factura y extraer: *Proveedor, Número de factura, Fecha, Materiales/Líneas de producto, Base imponible, IVA y Total*.
   - Guarda el registro completo en la base de datos de **Google Sheets** adjuntando el enlace al archivo en Drive.

## 🛠️ Tecnologías Utilizadas

*   [**Make (Integromat)**](https://www.make.com/): Plataforma No-Code para orquestar la automatización.
*   [**Telegram Bot API**](https://core.telegram.org/bots): Interfaz de usuario sencilla y accesible en cualquier lugar.
*   [**OpenAI API**](https://openai.com/api/): Inteligencia artificial para transcripción (Whisper) y extracción de entidades y datos visuales (GPT-4o / GPT-4o-mini).
*   [**Google Sheets**](https://workspace.google.com/products/sheets/): Base de datos centralizada.
*   [**Google Drive**](https://workspace.google.com/products/drive/): Almacenamiento seguro de las facturas originales.

## 🚀 Cómo utilizar este proyecto

Para implementar esta automatización en tu propio entorno, sigue estos pasos:

### 1. Requisitos Previos
*   Una cuenta en [Make.com](https://make.com).
*   Un bot de Telegram (puedes crearlo gratis hablando con [BotFather](https://t.me/botfather) en Telegram).
*   Una cuenta de [OpenAI](https://platform.openai.com/) con saldo para llamadas a la API.
*   Una cuenta de Google (para Sheets y Drive).

### 2. Configurar Google Sheets
Crea un documento de Google Sheets con una pestaña llamada `Base de Datos - Trabajos Electricidad` y asegúrate de añadir las siguientes columnas:
*   Fecha
*   Cliente
*   Horas_Trabajadas
*   Materiales_Audio (Materiales de trabajo)
*   Enlace (Para la factura en Drive)
*   Materiales_Factura
*   Base_Imponible_EUR
*   IVA_EUR
*   Total_Factura_EUR

### 3. Importar el Blueprint a Make
1. Crea un nuevo escenario en Make.
2. Haz clic en el botón de tres puntos (Más opciones) en la parte inferior de la pantalla y selecciona **"Import Blueprint"**.
3. Sube el archivo `blueprint.json` incluido en este repositorio.

### 4. Configurar Conexiones
Una vez importado el escenario, verás varios módulos con errores. Haz clic en ellos para configurar (o reconectar) tus propias credenciales:
*   **Módulos de Telegram:** Añade el Token de tu bot proporcionado por BotFather.
*   **Módulos de OpenAI:** Añade tu API Key de OpenAI.
*   **Módulos de Google Drive y Sheets:** Inicia sesión con tu cuenta de Google. Selecciona la carpeta de Drive donde quieres guardar las facturas y vincula el Spreadsheet y la Hoja que creaste en el Paso 2.

### 5. ¡Poner en marcha!
Guarda el escenario y enciéndelo. ¡Ya puedes enviar audios y fotos a tu bot de Telegram y ver la magia ocurrir en tu hoja de cálculo!

## 🤝 Contribuir
Si tienes sugerencias para mejorar este bot, ¡las pull requests son bienvenidas!

## 📄 Licencia
Este proyecto es de código abierto y está disponible bajo la licencia [MIT](LICENSE).
