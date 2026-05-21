# Proyecto ML5 - Reconocimiento de Imágenes y Detección en Tiempo Real

## 📋 Descripción

Proyecto educativo que utiliza **ML5.js** para crear aplicaciones web con inteligencia artificial. Incluye dos funcionalidades principales:

1. **Clasificación de Imágenes** - Reconoce qué objeto hay en una imagen estática
2. **Detección en Tiempo Real** - Detecta objetos a través de la cámara web con barras de confianza

---

## 🛠️ Tecnologías Utilizadas

### **Librerías**
- **[p5.js](https://p5js.org/)** - Librería JavaScript para gráficos y canvas
- **[ML5.js](https://learn.ml5js.org/)** - Librería de Machine Learning accesible y fácil de usar
- **[MobileNet](https://github.com/tensorflow/tfjs-models/tree/master/mobilenet)** - Modelo preentrenado para clasificación de imágenes (1000 clases de objetos)

### **Herramientas**
- HTML5
- CSS3
- JavaScript (Vanilla)
- Git & GitHub

---

## 📁 Estructura del Proyecto

```
ML5-Proyecto/
├── README.md                 # Este archivo
├── imagenes1.html           # Clasificador de imágenes simple
├── imagenes2.html           # Variante del clasificador
├── imagenes3.html           # Variante del clasificador
├── mimodelo.html            # Detector en tiempo real con modelo personalizado
├── image/                   # Carpeta de imágenes de ejemplo
│   ├── 1.jpg
│   ├── 2.jpg
│   ├── leon.jpg
│   ├── oso.jpg
│   └── vaca-1.jpg
└── model/                   # Modelo entrenado con Teachable Machine
    ├── model.json          # Arquitectura del modelo
    ├── metadata.json       # Información del modelo
    └── weights.bin         # Pesos entrenados
```

---

## 🚀 Cómo Usar

### **1. Clasificador de Imágenes (`imagenes1.html`)**

```html
<!-- Abre el archivo en el navegador -->
<!-- Selecciona una imagen del dropdown -->
<!-- El sistema la clasifica automáticamente -->
```

**Resultado esperado:**
- Muestra la imagen en el canvas (500x500)
- Debajo aparece: `Animal: [nombre] - [porcentaje]%`
- Usa modelo MobileNet (pre-entrenado de Google)

**Funcionalidades:**
- Carga la imagen cuando la seleccionas
- Espera a que cargue completamente antes de clasificar
- Muestra solo la predicción principal

---

### **2. Detector en Tiempo Real (`mimodelo.html`)**

```html
<!-- Abre el archivo en el navegador -->
<!-- Permite acceso a la cámara web -->
<!-- Detecta objetos continuamente -->
```

**Resultado esperado:**
- Video en vivo de la cámara (320x260)
- 5 barras de confianza para cada clase:
  - Celular
  - Cable
  - Audífonos
  - Juego
  - Billetera
- Las barras se llenan según el objeto detectado

**Funcionalidades:**
- Detección en tiempo real
- Barras visuales verdes que muestran confianza (0-100%)
- Compacto y simple (30% ancho, 15px alto)
- Porcentaje al lado de cada barra

---

## 🧠 Modelos Utilizados

### **MobileNet (imagenes1.html)**
- **Origen:** [Google TensorFlow.js Models](https://github.com/tensorflow/tfjs-models/tree/master/mobilenet)
- **Capacidad:** Clasifica 1000 categorías diferentes
- **Ventaja:** Rápido y ligero para navegadores
- **Uso:** Identificar animales, objetos comunes, etc.

### **Modelo Personalizado (mimodelo.html)**
- **Herramienta de entrenamiento:** [Google Teachable Machine](https://teachablemachine.withgoogle.com/)
- **Clases entrenadas:** 5 objetos personalizados
  - Celular
  - Cable
  - Audífonos
  - Juego
  - Billetera
- **Datos:** Imágenes capturadas desde cámara web
- **Formato:** COCO-SSD (exportado como Teachable Machine)

---

## 💻 Requisitos

### **Navegador**
- Chrome, Firefox, Safari o Edge reciente
- Soporte para WebGL (para TensorFlow.js)
- Cámara web (para `mimodelo.html`)

### **Servidor Local** (Recomendado)
Para evitar errores de CORS, ejecuta un servidor local:

```bash
# Con Python 3
python -m http.server 8000

# Con Node.js
npx http-server

# Con Ruby
ruby -run -ehttpd . -p8000
```

Luego abre:
- `http://localhost:8000/imagenes1.html`
- `http://localhost:8000/mimodelo.html`

---

## 📚 Fuentes de Inspiración

1. **[ML5.js Official Documentation](https://learn.ml5js.org/)** - Documentación oficial
2. **[p5.js Reference](https://p5js.org/reference/)** - Referencia de p5.js
3. **[Google Teachable Machine](https://teachablemachine.withgoogle.com/)** - Para entrenar modelos personalizados
4. **[TensorFlow.js](https://www.tensorflow.org/js)** - Backend de ML5.js

---

## 🎯 Casos de Uso

✅ **Educativo:** Aprender Machine Learning desde el navegador  
✅ **Prototipado:** Crear demostraciones rápidas de IA  
✅ **Interactivo:** Desarrollar aplicaciones web con IA  
✅ **Sin servidor:** No requiere backend costoso

---

## 📝 Notas Técnicas

### **¿Por qué el callback en loadImage()?**
```javascript
img = loadImage('image/foto.jpg', function() {
    classifier.classify(img, gotResult);
});
```
- `loadImage()` es **asíncrono** (carga en background)
- El callback espera a que termine antes de clasificar
- Sin callback: clasifica antes de cargar = error

### **Barras Compactas**
- Ancho: 30% (no ocupan toda la pantalla)
- Alto: 15px (suficientemente visibles)
- Gap: 5px (porcentaje muy cerca)
- Layout: Nombre | Barra | Porcentaje

---

## 🐛 Solución de Problemas

| Problema | Solución |
|----------|----------|
| "Modelo no carga" | Usa servidor local, no abras desde archivo |
| "Cámara no funciona" | Permite permisos en el navegador |
| "Imágenes se ven pixeladas" | Aumenta tamaño del canvas |
| "Clasificación lenta" | MobileNet es normal (es preciso) |

---

## 👨‍💻 Autor

**Pineda-25**  
Email: juniorpineda2511@gmail.com  
GitHub: [Pineda-25](https://github.com/Pineda-25)

---

## 📄 Licencia

Este proyecto es de código abierto y está disponible bajo la Licencia MIT.

Las librerías utilizadas tienen sus propias licencias:
- **p5.js:** LGPL 2.1
- **ML5.js:** MIT
- **TensorFlow.js:** Apache 2.0

---

## 🎓 Aprendizajes Clave

1. **ML5.js simplifica TensorFlow.js** - Acceso fácil a modelos sin complejidad
2. **Asincronía en JavaScript** - Callbacks y promises son esenciales
3. **Canvas para visualización** - p5.js facilita dibujar y actualizar gráficos
4. **Modelos pre-entrenados** - No necesitas entrenar desde cero
5. **Machine Learning en el navegador** - Privacidad: todo ocurre localmente

---

**Última actualización:** 21 de Mayo de 2026
