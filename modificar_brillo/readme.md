Script para modificar el brillo de un lote de imagenes

## Tabla de contenidos
[1. Version 1](https://github.com/TadeoRiganti/editar_imagenes_en_lote/wiki/Modificar-brillo#versi%C3%B3n-1)
   1. [Sobre el metodo](https://github.com/TadeoRiganti/editar_imagenes_en_lote/wiki/Modificar-brillo#sobre-el-metodo)
   1. [Estructura del código](https://github.com/TadeoRiganti/editar_imagenes_en_lote/wiki/Modificar-brillo#estructura-del-c%C3%B3digo)
   1. [Uso](https://github.com/TadeoRiganti/editar_imagenes_en_lote/wiki/Modificar-brillo#uso)
      1. [Requisitos previos](https://github.com/TadeoRiganti/editar_imagenes_en_lote/wiki/Modificar-brillo#requisitos-previos)
   1. [Analisis del código](https://github.com/TadeoRiganti/editar_imagenes_en_lote/wiki/Modificar-brillo#analisis-del-c%C3%B3digo)
      1. [Script](https://github.com/TadeoRiganti/editar_imagenes_en_lote/wiki/Modificar-brillo#script)
      1. [Resumen](https://github.com/TadeoRiganti/editar_imagenes_en_lote/wiki/Modificar-brillo#resumen)
      1. [Pasos](https://github.com/TadeoRiganti/editar_imagenes_en_lote/wiki/Modificar-brillo#1-importar-librerias)

<hr>
<br>

# Versión 1

## Sobre el metodo
*   **Titulo:** Script - Modificar brillo en lote v1
*   **Descripción general:** Script de Python para modificar el brillo de todas las imagenes del directorio proporcionado.
*   **Fuente:** Google Gemini 
*   **Fecha de creación:**  27/11/24

### Objetivo

Modificar el brillo de todas las imagenes del directorio objetivo.
Sobreescribir las imagenes.

### Ejemplos de uso

Aumentar el brillo en un factor de 20%
Reducir el brillo en un facor de 30%.

## Estructura del código

###  Descripción de modulos

#### Función principal

*   **Propósito:** procesar un conjunto de imágenes de forma automatizada, ajustando el brillo de cada una de ellas en un porcentaje específico. Esta tarea se realiza iterando sobre un directorio de imágenes, aplicando la modificación deseada y guardando el resultado en el mismo directorio o en uno nuevo. 
<hr>

*   **Entradas:** 
    * **Directorio de imágenes**: La ruta completa al directorio donde se encuentran las imágenes a procesar.
    * **Factor de ajuste de brillo**: Un número decimal que indica el porcentaje en que se aumentará o disminuirá el brillo de las imágenes. Por ejemplo, un valor de 1.2 aumentará el brillo en un 20%. 
<hr>

*   **Salidas:** 
    * **Imágenes modificadas**: Las imágenes originales con el brillo ajustado, guardadas en el mismo directorio. 
<hr>

*   **Lógica:** 
1. **Definición de la función de ajuste de brillo**: 
   1. Se crea una función que toma como entrada una imagen y un factor de ajuste.
   1. La función itera sobre cada píxel de la imagen, modificando los valores de los canales de color (rojo, verde y azul) según el factor de ajuste.
   1. Se aplican límites para asegurar que los valores de los píxeles no excedan el rango válido (0-255).
<br>

2. **Obtención del directorio de imágenes**:
   1. Se establece de forma predeterminada el directorio donde se encuentran las imágenes.
<br>

3. **Iteración sobre las imágenes**:
   1. Se recorre cada archivo en el directorio especificado.
   1. Se verifica que el archivo tenga una extensión de imagen válida (por ejemplo, .jpg, .png).
<br>

4. **Apertura y procesamiento de la imagen**:
   1. Se abre la imagen utilizando la biblioteca Pillow.
   1. Se llama a la función de ajuste de brillo para modificar la imagen.
<br>

5. **Guardado de la imagen modificada**:
   1. Se guarda la imagen modificada en el mismo directorio y con el mismo nombre.

## Uso

### Requisitos previos

* 

## Analisis del código

### Script

```
from PIL import Image

def ajustar_brillo(imagen, factor):
    """Ajusta el brillo de una imagen.

    Args:
        imagen: La imagen a modificar.
        factor: Factor de ajuste del brillo (1.0 para sin cambios).

    Returns:
        La imagen con el brillo ajustado.
    """

    imagen = imagen.convert('RGB')
    width, height = imagen.size
    for x in range(width):
        for y in range(height):
            r, g, b = imagen.getpixel((x, y))
            r = int(min(255, max(0, r * factor)))
            g = int(min(255, max(0, g * factor)))
            b = int(min(255, max(0, b * factor)))
            imagen.putpixel((x, y), (r, g, b))
    return imagen

# Directorio donde se encuentran las imágenes
directorio_imagenes = "ruta/a/tu/carpeta/de/imagenes"

# Recorre todas las imágenes en el directorio
for archivo in os.listdir(directorio_imagenes):
    if archivo.endswith(".jpg") or archivo.endswith(".png"):  # Ajusta las extensiones según tus necesidades
        ruta_imagen = os.path.join(directorio_imagenes, archivo)
        imagen = Image.open(ruta_imagen)
        imagen_ajustada = ajustar_brillo(imagen, 1.2)  # Aumenta el brillo en un 20%
        imagen_ajustada.save(ruta_imagen)
```

### Resumen

1. Se importa la biblioteca Pillow.
2. Se define una función para ajustar el brillo de una imagen.
3. Se especifica el directorio donde se encuentran las imágenes.
4. Se itera sobre cada archivo en el directorio.
5. Se verifica si el archivo es una imagen.
6. Se abre la imagen y se ajusta su brillo.
7. Se guarda la imagen modificada.

En cada iteración del bucle, se procesa una imagen, ajustando su brillo y guardando el resultado sobre el mismo archivo.

### Pasos

#### 1) Importar librerias: 
```
from PIL import Image
```
* **¿Por que?** Importamos la biblioteca Pillow (PIL Fork), que es la herramienta principal para trabajar con imágenes en Python. Esta biblioteca nos proporciona una interfaz sencilla para abrir, manipular y guardar imágenes en diversos formatos.
<br>

#### 2) Definición de la función de ajuste de brillo: 
```
def ajustar_brillo(imagen, factor):
    # ... (código de la función)
```
* **¿Qué hace?** Esta función es el corazón del script. Toma como entrada una imagen y un factor de ajuste y devuelve la imagen con el brillo modificado.
* **¿Cómo funciona?**
   * **Conversión a RGB**: Se asegura de que la imagen esté en modo RGB para poder manipular los canales de color individualmente.
   * **Iteración sobre los píxeles**: Recorre cada píxel de la imagen.
   * **Modificación de los canales**: Multiplica los valores de cada canal (rojo, verde, azul) por el factor de ajuste.
   * **Limitación de valores**: Se asegura de que los valores de los píxeles no se salgan del rango válido (0-255).
<br>

#### 3) Obtención del directorio de imágenes:
```
directorio_imagenes = "ruta/a/tu/carpeta/de/imagenes"
```
* **¿Por qué?** Se establece la ruta al directorio donde se encuentran las imágenes que queremos procesar. 
<br>

#### 4) Iteración sobre las imágenes:
```
for archivo in os.listdir(directorio_imagenes):
    # ... (código dentro del bucle)
```
* **¿Qué hace?** Este bucle recorre cada archivo dentro del directorio especificado.
<br>

#### 5) Verificación de la extensión:
```
if archivo.endswith(".jpg") or archivo.endswith(".png"):
    # ...
```
* **¿Por qué?** Se verifica si el archivo tiene una extensión de imagen válida (en este caso, .jpg o .png). Esto nos permite procesar solo las imágenes y omitir otros tipos de archivos.
<br>

#### 6) Apertura y procesamiento de la imagen:
```
ruta_imagen = os.path.join(directorio_imagenes, archivo)
imagen = Image.open(ruta_imagen)
imagen_ajustada = ajustar_brillo(imagen, 1.2)
```
* **¿Qué hace?**
   * Se construye la ruta completa a la imagen.
   * Se abre la imagen utilizando la función open de Pillow.
   * Se llama a la función ajustar_brillo para modificar la imagen.
<br>

#### 7) Guardado de la imagen modificada:
```
imagen_ajustada.save(ruta_imagen)
```
* **¿Qué hace?** Se guarda la imagen modificada en el mismo directorio con el mismo nombre, sobrescribiendo la imagen original.
<br>

