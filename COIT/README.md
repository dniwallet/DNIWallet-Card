# Tarjeta del COIT

Pasos
* Imagen gráfica del fondo
* Identificar que campos del DNI se utilizarán en la tarjeta. Tipicamente el nombre completo y la fotografía

## Imagen gráfica del fondo
Utiliza un editor de imágenes para crear el fondo de la tarjeta. No dibujes los campos que va a rellenar DNI Wallet.

![Tarjeta COIT](images/coit.webp)

El fondo de la tarjeta es:

![Tarjeta COIT](images/front.webp)

[front.webp](images/front.webp)

DNI Wallet añadirá al fondo los campos dinámicos necesarios para crear la tarjeta final de cada persona.

## HTML de la Tarjeta

Este es el código HTML plano para la tarjeta. Al no utilizar frameworks adicionales la tarjeta se dibujará lo más rápidamente posible.

```html
<html lang="es">
<head>
  <meta charset="utf-8">
  <title>Tarjeta Colegiado COIT</title>
  <meta name="description" content="Tarjeta Colegiado COIT">
  <meta name="author" content="DNI Wallet">
  <link rel="stylesheet" href="front.css">
</head>
<body>
  <div id=dniwallet_front>
    <div id="card_front"></div>
    <div id="dni_picture"></div>
    <span id="dni_fullname">CARMEN ESPAÑOLA ESPAÑOLA</span>
    <span id="coit_dni">DNI: <span id="dni_number">99999999R</span></span>
    <span id="coit_colegiado">COLEGIADO: 9.999</span>
    <span id="coit_fecha">22/09/2004</span>
  </div>
</body>
</html>
```
[front.html](front.html)

La página HTML sólo tiene la definición de campos de la tarjeta:
| Campo | Descripción | Origen |
| ----- | ----------- | ------ |
| **card_front**     | Fondo | Imagen de fondo de la tarjeta | 
| **dni_picture**    | Fotografía | Documento de identidad | 
| **dni_fullname**   | Nombre completo | Documento de identidad | 
| **dni_number**     | Número de DNI |  Documento de identidad | 
| **coit_colegiado** | Número de colegiado | proporcionado por el COIT |
| **coit_fecha**     | Desde cuando es colegiado | proporcionado por el COIT |

Los elementos **div** los utilizamos para definir imágenes (el fondo y la fotografía)
Los elementos **span** los utilizamos para definir campos de texto.

## CSS de la Tarjeta 

En [front.css](front.css) están los estilos para dibujar la tarjeta. A continuación lo explicamos por partes:

Todos los elementos tienen posicionamiento absoluto porque vamos a dibujar campos de texto encima del fondo.
```css
position: absolute;
```

Una tarjeta DNI Wallet siempre tiene tamaño 1024x652:
```css
html, body{ margin: 0; }
body { background: #d5d5d5; }
html, body, #dniwallet_front { 
  width: 1024px;
  height: 652px;
  position: absolute;
}
```

Los elementos **div** los utilizamos para definir imágenes (el fondo y la fotografía). Tienen posición absoluta.
```css
div {
  position: absolute;
}
```

Los elementos **span** los utilizamos para definir campos de texto. Por defecto tienen el font **Arial Narrow** de **35 pixels**, alineamiento a la izquierda, y color blanco (**#fff**)
```css
span {
  position: absolute;
  font-family: Arial Narrow, sans-serif;
  font-size: 35px;
  font-weight: normal;
  letter-spacing: 0;
  text-align: left;
  color: #fff;
}
```

### Imagen del fondo

Situada en la coordenada (0,0), con tamaño 1024x652 e imagen de fondo **front.webp**
```css
#card_front { 
  left: 0px;
  top: 0px;
  width: 1024px;
  height: 652px;
  background-image: url(images/front.webp);
  background-repeat: no-repeat;
  background-size: cover;
}
```

### Fotografia
![carmen](images/carmen.webp)

Situada en la coordenada (788,21), con tamaño 229x281 **carmen.webp**
```css
#dni_picture { 
  left: 788px;
  top: 21px;
  width: 229px;
  height: 281px;
  background-image: url(images/carmen.webp);
  background-repeat: no-repeat;
  background-size: cover;
}
```

### Nombre completo
Situado en la coordenada (54,435), con tamaño 944x66
```css
#dni_fullname { 
  left: 54px;
  top: 435px;
  width: 944px;
  height: 66px;
}
```

### Número de DNI
Situado en la coordenada (54,481), con tamaño 944x66
```css
#coit_dni { 
  left: 54px;
  top: 481px;
  width: 944px;
  height: 66px;
}
```

### Número de Colegiado
Situado en la coordenada (54,526), con tamaño 944x66
```css
#coit_colegiado { 
  left: 54px;
  top: 526px;
  width: 944px;
  height: 66px;
}    
```

### Fecha de Colegiación
Situado en la coordenada (54,572), con tamaño 944x66
```css
#coit_fecha { 
  left: 54px;
  top: 572px;
  width: 944px;
  height: 66px;
}
```

## License

MIT License

Copyright (c) 2023 DNI Wallet

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
