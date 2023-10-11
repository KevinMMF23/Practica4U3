# Tienda en Línea

## Introducción

Bienvenido a la documentación de la Tienda en Línea, una aplicación web simple para mostrar un catálogo de productos, permitir a los usuarios agregar productos a un carrito de compras y mostrar un resumen de la compra. Este proyecto se basa en HTML, CSS y JavaScript, y utiliza la biblioteca Bootstrap para la interfaz de usuario.

## Índice

1. [Herramientas Utilizadas](#herramientas-utilizadas)
2. [Teoría](#teoría)
3. [Ejemplos de Código](#ejemplos-de-código)
4. [Preguntas Frecuentes](#preguntas-frecuentes)
5. [Conclusión](#conclusión)
6. [Descarga e Instalación](#descarga-e-instalación)

## Herramientas Utilizadas

- HTML
- CSS
- JavaScript
- Bootstrap

## Teoría

La aplicación se basa en la manipulación del DOM (Document Object Model) con JavaScript. El catálogo de productos se almacena en una matriz (`catalogo`) y se muestra en la página mediante la generación de tarjetas de productos dinámicamente. Los usuarios pueden agregar productos al carrito, que se almacena en una matriz (`carrito`). El resumen de la compra se actualiza en tiempo real y se muestra en la página.

## Ejemplos de Código

A continuación, se presentan ejemplos de código destacados de la aplicación:

### 1. Generación de Tarjetas de Productos

El siguiente código muestra cómo se generan las tarjetas de productos en el catálogo y se agregan al DOM:

```javascript
// Ejemplo de código para la generación de tarjetas de productos
catalogo.forEach((producto) => {
    const card = document.createElement("div");
    card.classList.add("col-md-4", "mb-4");
    card.innerHTML = `
        <div class="card">
            <img src="${producto.imagen}" class="card-img-top" alt="Producto ${producto.id}">
            <div class="card-body">
                <h5 class="card-title">Producto ${producto.id}</h5>
                <p class="card-text">Precio: $${producto.precio}</p>
                Cantidad: <input type="number" id="cantidadProducto${producto.id}" value="0" min="0">
                <button class="btn btn-primary" id="agregar${producto.id}">Agregar al Carrito</button>
            </div>
        </div>
    `;
    catalogoContainer.appendChild(card);
});
```
### 1. Manipulación del carrito
```javascript
// Ejemplo de código para la manipulación del carrito
function agregarProductoAlCarrito(producto, cantidad) {
    const productoEnCarrito = carrito.find((item) => item.producto.id === producto.id);

    if (productoEnCarrito) {
        productoEnCarrito.cantidad += cantidad;
    } else {
        carrito.push({ producto, cantidad });
    }

    actualizarResumenCompra();
}
```
### 1. Manejador de eventos
```javascript
// Ejemplo de código para el manejador de eventos
const finalizarCompraButton = document.getElementById("finalizarCompra");
finalizarCompraButton.addEventListener("click", function () {
    sessionStorage.setItem("carrito", JSON.stringify(carrito));
    window.location.href = "resultados.html";
});
```
## Preguntas frecuentes

1. ¿Qué tipo de variable es "catalogo" y cómo se manipula?
"catalogo" es una matriz en JavaScript que almacena objetos con información de productos. Se manipula mediante bucles y métodos para recorrer y acceder a los datos de los productos.

2. ¿Qué hace const card = document.createElement("div")?
const card crea un nuevo elemento HTML <div> en el DOM. Esto se utiliza para generar tarjetas de productos que se mostrarán en la página.

3. ¿Qué hace card.innerHTML?
card.innerHTML establece el contenido HTML de un elemento creado anteriormente (card). En el ejemplo, se utiliza para construir el contenido de la tarjeta de producto.

4. ¿Qué hace catalogoContainer.appendChild(card)?
catalogoContainer.appendChild(card) agrega la tarjeta de producto (card) como un hijo del elemento con el ID "catalogoContainer". Esto muestra la tarjeta de producto en la página.

## Conclusión

La aplicación de Tienda en Línea demuestra cómo se pueden utilizar HTML, CSS y JavaScript para crear una experiencia de compra simple en línea. Los ejemplos de código proporcionados son un punto de partida para desarrollar aplicaciones más complejas.

## Descarga e Instalación

### 1. Para ejecutar esta aplicación localmente, sigue estos pasos:
 Descarga los archivos HTML, CSS y JavaScript, descomprime el archivo y abre index.html.
