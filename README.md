# 🗺️ Simulador 3D de Terreno y Lluvia con Ajuste Polinomial GeoTIFF

Una aplicación web interactiva desarrollada, desde el semillero SiMULa de la Universidad Militar Nueva Granada, que permite cargar modelos de elevación digital (DEM) en formato GeoTIFF, extraer una región de interés (ROI) de forma gráfica, realizar una regresión polinomial sobre el terreno seleccionado y visualizar una simulación física de escorrentía de agua (lluvia) en 3D calculada en tiempo real.

---

## 📝 Encuesta de Usabilidad
Tu opinión es fundamental para mejorar esta herramienta. Si has probado la aplicación, te invitamos a responder nuestra breve encuesta de usabilidad:
👉 **[Completar Encuesta de Usabilidad](https://docs.google.com/forms/d/e/1FAIpQLSfmFKdazC5dCiUh8aXNSm7JLOGqVtdNx0JjEWu16Z49qoF04A/viewform?usp=publish-editor)**

---

## ✨ Características Principales

*   **Procesamiento Local de GeoTIFF:** Lectura y decodificación de archivos `.tif` directamente en el navegador del usuario utilizando `geotiff.js`, garantizando la privacidad sin necesidad de subir datos a un servidor.
*   **Selección Dinámica de ROI (2D):** Visualización del ráster en un mapa 2D con un recuadro interactivo (arrastrable y redimensionable) para delimitar exactamente el área de estudio.
*   **Ajuste Matemático del Terreno:** Aplicación de mínimos cuadrados para realizar una regresión polinomial bivariada de la región seleccionada. El usuario puede elegir el **grado del polinomio (1 al 5)**.
*   **Métricas en Tiempo Real:** Cálculo automático y visualización del Error Cuadrático Medio (**RMSE** en metros) para evaluar la precisión del ajuste del polinomio frente a los datos originales del GeoTIFF.
*   **Simulación Física 3D (RK4):** Motor de partículas personalizado que simula la caída y flujo del agua utilizando el método de integración de Runge-Kutta de cuarto orden (RK4) para el cálculo preciso de gradientes y colisiones.
*   **Control Total del Entorno:**
    *   Escala Z para exagerar el relieve.
    *   Intensidad de la lluvia y altura de caída de las gotas.
    *   Gravedad y coeficientes de fricción del terreno ajustables.
    *   Modos de lluvia: Continua, Tormenta (aleatoria) y Puntual.
*   **Cámara Interactiva:** Rotación panorámica y ajuste de inclinación mediante el arrastre del ratón, con zoom (escala Z) accesible mediante la rueda del ratón.

## 🛠️ Tecnologías Utilizadas

*   **Frontend:** HTML5, CSS3, Vanilla JavaScript (ES6+).
*   **Renderizado:** Canvas API (Motor de proyección isométrica 3D propio, sin dependencias pesadas como WebGL o Three.js).
*   **Origen de Datos y Procesamiento:** Los datos de elevación en formato `.tif` fueron descargados de **Google Earth Engine** y se leen localmente utilizando la biblioteca de terceros [geotiff.js](https://geotiffjs.github.io/) (vía CDN) para extraer la información del terreno.

## 🚀 Instalación y Uso

Dado que es una aplicación basada completamente en tecnologías web del lado del cliente, no requiere instalación compleja ni configuraciones de servidor.

1.  **Descargar y Descomprimir:**
    Descarga el archivo `Simulacion_Lluvia_final.zip` y extrae su contenido en una carpeta de tu computadora. Al descomprimirlo, encontrarás el código fuente (`Simulacion_Lluvia_final.html`) junto con dos imágenes de elevación de prueba en formato `.tiff`.

2.  **Abrir la aplicación:**
    Simplemente haz doble clic en el archivo `Simulacion_Lluvia_final.html` para abrirlo en cualquier navegador web moderno (Chrome, Firefox, Edge, Safari). 
    *(Nota: Algunas funciones estrictas de seguridad local de los navegadores podrían requerir que abras el archivo a través de un servidor local simple, como la extensión "Live Server" en VSCode o ejecutando `python -m http.server` desde tu terminal en la carpeta extraída).*

3.  **Probar el simulador:**
    En la pantalla inicial de la aplicación, utiliza el botón de carga para seleccionar una de las dos imágenes `.tiff` que venían incluidas en el `.zip` y explora la simulación al instante.

## 📖 Guía de Interacción

1.  **Carga:** En la pantalla inicial, selecciona un archivo GeoTIFF válido y define el grado del polinomio deseado.
2.  **Ajuste de Área (Panel Izquierdo):** Utiliza el recuadro naranja sobre el mapa 2D. Arrastra desde el centro para moverlo, o desde los bordes para redimensionarlo. El modelo 3D se recalculará automáticamente al soltar el clic.
3.  **Controles de Cámara (Panel Derecho):**
    *   **Click Izquierdo + Arrastrar:** Gira e inclina el modelo 3D.
    *   **Rueda del ratón:** Ajusta la exageración vertical (Escala Z).
4.  **Parámetros Físicos:** Utiliza los controles deslizantes para cambiar la gravedad, fricción, altura y cantidad de partículas, observando los cambios instantáneamente en el panel de estadísticas.

---
*Desarrollado para el análisis interactivo de modelos de elevación y dinámicas de fluidos superficiales.*
