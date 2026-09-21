# Laboratorio #4 - CRUD de Productos

**Fecha:** 21/09/2026

## Contenido del Repositorio

Este repositorio contiene el desarrollo del **Laboratorio #4** de la materia **HPA III**, utilizando el lenguaje de programación **C#**, Windows Forms y una base de datos **SQL Server**.

La actividad consiste en desarrollar una aplicación para la gestión de productos mediante operaciones **CRUD (Crear, Leer, Actualizar y Eliminar)**.

El sistema permite registrar productos con los siguientes datos:

- ID
- Nombre
- Precio
- Cantidad
- Imagen

La aplicación cuenta con una interfaz gráfica que permite realizar las operaciones directamente desde el formulario y visualizar los registros almacenados en la base de datos mediante un `DataGridView`.

El proyecto está compuesto principalmente por las clases `Conexion` y `Producto`, además del formulario principal `Form1` y el archivo `Program.cs` que contiene el punto de entrada de la aplicación.

---

## Tecnologías Utilizadas

- **Lenguaje:** C#
- **Framework:** .NET
- **Tipo de aplicación:** Windows Forms
- **IDE:** Visual Studio
- **Base de datos:** Microsoft SQL Server
- **Conector:** Microsoft.Data.SqlClient
- **Control de datos:** DataGridView
- **Control de imágenes:** PictureBox
- **Selección de archivos:** OpenFileDialog
- **Manejo de imágenes:** MemoryStream
- **Control de versiones:** Git / GitHub

---
## 🗄️ Implementación y Uso de SQL Server

Para la persistencia de los datos, se utilizó **Microsoft SQL Server** conectado a través de ADO.NET. El manejo de la base de datos destaca por las siguientes prácticas:

1. **Estructura de la Tabla:** Se utilizó el tipo de dato `VARBINARY(MAX)` para almacenar las imágenes directamente en la base de datos, garantizando que la información visual viaje junto con los datos del producto.
   ```sql
   CREATE TABLE productos (
       id INT IDENTITY(1,1) PRIMARY KEY,
       nombre VARCHAR(100) NOT NULL,
       precio DECIMAL(10,2) NOT NULL,
       cantidad INT NOT NULL,
       imagen VARBINARY(MAX) NULL
   );

## Capturas de Pantalla y Problemas

### 1. Interfaz Principal

La aplicación cuenta con una interfaz gráfica diseñada para administrar los productos registrados en la base de datos.

La ventana contiene campos para ingresar el nombre, precio y cantidad del producto, además de un área para seleccionar y visualizar una imagen.

También cuenta con los botones:

- Agregar
- Modificar
- Eliminar
- Limpiar
- Salir

Además, se incluye un campo de búsqueda y un `DataGridView` para mostrar los productos registrados.

#### Interfaz Principal

<!-- Colocar aquí la captura de pantalla de la interfaz principal -->

![Interfaz Principal](./capturas/interfaz-principal.png)

---

### 2. Agregar Producto

El botón **Agregar** permite registrar un nuevo producto en la base de datos.

Antes de realizar la inserción, el programa valida que el nombre no esté vacío y que los campos de precio y cantidad contengan valores válidos.

Después de realizar correctamente la operación, los datos se limpian y el `DataGridView` se actualiza para mostrar el nuevo registro.

#### Captura del proceso de agregar

<!-- Colocar aquí la captura de pantalla del producto antes o durante el registro -->

![Agregar Producto](./capturas/agregar-producto.png)

#### Producto agregado

<!-- Colocar aquí la captura mostrando el producto registrado en el DataGridView -->

![Producto Agregado](./capturas/producto-agregado.png)

---

### 3. Modificar Producto

El botón **Modificar** permite actualizar los datos de un producto previamente seleccionado en el `DataGridView`.

Al seleccionar una fila, los datos del producto son cargados nuevamente en los campos del formulario para poder modificarlos.

Después de realizar la actualización, el sistema refresca el contenido del `DataGridView`.

#### Captura del proceso de modificación

<!-- Colocar aquí la captura de la modificación -->

![Modificar Producto](./capturas/modificar-producto.png)

---

### 4. Eliminar Producto

El botón **Eliminar** permite eliminar un producto seleccionado de la base de datos.

Antes de realizar la eliminación, el programa presenta un mensaje de confirmación para verificar la acción del usuario.

#### Confirmación de eliminación

<!-- Colocar aquí la captura del mensaje de confirmación -->

![Confirmar Eliminación](./capturas/confirmar-eliminacion.png)

#### Resultado de la eliminación

<!-- Colocar aquí la captura después de eliminar el producto -->

![Producto Eliminado](./capturas/producto-eliminado.png)

---

### 5. Búsqueda de Productos

La aplicación posee un campo de **Búsqueda** que permite filtrar dinámicamente los productos registrados.

La búsqueda se ejecuta mientras el usuario escribe y permite realizar consultas utilizando el nombre o el ID del producto.

#### Captura de la búsqueda

<!-- Colocar aquí la captura de pantalla de la búsqueda -->

![Búsqueda de Productos](./capturas/busqueda-productos.png)

---

### 6. Selección de Imagen

La aplicación permite seleccionar una imagen desde el equipo utilizando el componente `OpenFileDialog`.

Los formatos de imagen aceptados son:

- `.jpg`
- `.jpeg`
- `.png`
- `.bmp`

La imagen seleccionada se muestra en el `PictureBox` antes de ser almacenada en la base de datos.

#### Captura de selección de imagen

<!-- Colocar aquí la captura del explorador de archivos o de la imagen seleccionada -->

![Selección de Imagen](./capturas/seleccion-imagen.png)

---

### 7. Almacenamiento de Imágenes

La imagen seleccionada se convierte a un arreglo de bytes utilizando `MemoryStream`.

Posteriormente, este arreglo `byte[]` es enviado a SQL Server para almacenarlo en el campo correspondiente de la tabla `productos`.

Cuando los productos son consultados nuevamente, la imagen es reconstruida para poder visualizarla dentro del `DataGridView`.

#### Captura de imagen almacenada

<!-- Colocar aquí la captura mostrando la imagen dentro del DataGridView -->

![Imagen del Producto](./capturas/imagen-producto.png)

---

### 8. Botón Limpiar

El botón **Limpiar** permite borrar los datos introducidos en los campos del formulario, restablecer la imagen predeterminada y quitar la selección actual del `DataGridView`.

#### Captura del botón Limpiar

<!-- Colocar aquí la captura del formulario después de utilizar Limpiar -->

![Limpiar Campos](./capturas/limpiar.png)

---

### 9. Botón Salir

El botón **Salir** permite cerrar la aplicación.

Antes de finalizar el programa, se muestra un mensaje de confirmación para verificar que el usuario realmente desea salir.

#### Confirmación de salida

<!-- Colocar aquí la captura del mensaje de confirmación -->

![Confirmar Salida](./capturas/confirmar-salida.png)

---

## Conceptos Aplicados

Durante el desarrollo de este laboratorio se aplicaron los siguientes conceptos:

### Programación Orientada a Objetos

Se utilizaron clases para organizar la estructura y funcionamiento de la aplicación.

Las principales clases utilizadas son:

```text
Conexion
Producto
Form1
