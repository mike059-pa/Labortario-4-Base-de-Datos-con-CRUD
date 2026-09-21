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

<img width="785" height="657" alt="image" src="https://github.com/user-attachments/assets/486f9cee-6d81-4069-bb79-e16effa8f91f" />


---

### 2. Agregar Producto

El botón **Agregar** permite registrar un nuevo producto en la base de datos.

Antes de realizar la inserción, el programa valida que el nombre no esté vacío y que los campos de precio y cantidad contengan valores válidos.

Después de realizar correctamente la operación, los datos se limpian y el `DataGridView` se actualiza para mostrar el nuevo registro.

#### Captura del proceso de agregar

<img width="766" height="647" alt="image" src="https://github.com/user-attachments/assets/2d65749f-286e-4ae1-a27b-1d2bb98ee601" />


<img width="950" height="657" alt="image" src="https://github.com/user-attachments/assets/78312b52-c37f-40b9-b2c9-a25f538bf381" />


#### Producto agregado

<!-- Colocar aquí la captura mostrando el producto registrado en el DataGridView -->

<img width="801" height="660" alt="image" src="https://github.com/user-attachments/assets/0c23924e-202b-414e-be35-53948394a0dc" />


---

### 3. Modificar Producto

El botón **Modificar** permite actualizar los datos de un producto previamente seleccionado en el `DataGridView`.

Al seleccionar una fila, los datos del producto son cargados nuevamente en los campos del formulario para poder modificarlos.

Después de realizar la actualización, el sistema refresca el contenido del `DataGridView`.

#### Captura del proceso de modificación


<img width="947" height="667" alt="image" src="https://github.com/user-attachments/assets/0efeb36f-be12-4ecb-bb7f-83223764c53d" />



---

### 4. Eliminar Producto

El botón **Eliminar** permite eliminar un producto seleccionado de la base de datos.

Antes de realizar la eliminación, el programa presenta un mensaje de confirmación para verificar la acción del usuario.

#### Confirmación de eliminación

<!-- Colocar aquí la captura del mensaje de confirmación -->

<img width="1002" height="686" alt="image" src="https://github.com/user-attachments/assets/17a55f0a-eccc-4f5b-b053-9ae4fe7c8e8a" />

<img width="941" height="652" alt="image" src="https://github.com/user-attachments/assets/3825e696-4b6e-4ff4-96a7-54588468b7da" />

#### Resultado de la eliminación

<!-- Colocar aquí la captura después de eliminar el producto -->

<img width="782" height="662" alt="image" src="https://github.com/user-attachments/assets/722422f3-76f5-4c35-a3fa-9a86f9c55fd4" />


---

### 5. Búsqueda de Productos

La aplicación posee un campo de **Búsqueda** que permite filtrar dinámicamente los productos registrados.

La búsqueda se ejecuta mientras el usuario escribe y permite realizar consultas utilizando el nombre o el ID del producto.

#### Captura de la búsqueda


<img width="775" height="652" alt="image" src="https://github.com/user-attachments/assets/2ada1146-06e1-4bc1-a8b2-8626707af136" />

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


---<img width="776" height="660" alt="image" src="https://github.com/user-attachments/assets/54f3bc76-4551-470f-bdd0-a42b15d50934" />


### 7. Almacenamiento de Imágenes

La imagen seleccionada se convierte a un arreglo de bytes utilizando `MemoryStream`.

Posteriormente, este arreglo `byte[]` es enviado a SQL Server para almacenarlo en el campo correspondiente de la tabla `productos`.

Cuando los productos son consultados nuevamente, la imagen es reconstruida para poder visualizarla dentro del `DataGridView`.

#### Captura de imagen almacenada

<!-- Colocar aquí la captura mostrando la imagen dentro del DataGridView -->

<img width="785" height="637" alt="image" src="https://github.com/user-attachments/assets/399d3382-0fc6-44c2-82e7-d519978a9dde" />




### 9. Botón Salir

El botón **Salir** permite cerrar la aplicación.

Antes de finalizar el programa, se muestra un mensaje de confirmación para verificar que el usuario realmente desea salir.

#### Confirmación de salida

<!-- Colocar aquí la captura del mensaje de confirmación -->

<img width="777" height="657" alt="image" src="https://github.com/user-attachments/assets/2f519b0b-6cd4-4057-a854-070896a4c7ca" />


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


## Instrucciones de Ejecución / Uso

### 1. Descargar el proyecto

El proyecto se encuentra comprimido en **7 partes RAR**. Es necesario descargar **las 7 partes** y colocarlas en la misma carpeta antes de iniciar la extracción.

Las partes deben tener una estructura similar a:

```text
Laboratorio_4.part1.rar
Laboratorio_4.part2.rar
Laboratorio_4.part3.rar
Laboratorio_4.part4.rar
Laboratorio_4.part5.rar
Laboratorio_4.part6.rar
Laboratorio_4.part7.rar
```
# Autor y Contexto

Nombre: Michael Hunt
Materia: HPA III
Institución: Universidad Tecnológica de Panamá (UTP)
Fecha de Realización: [21/09/2026]
