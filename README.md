# Tienda Online — Flask + PostgreSQL

Proyecto académico (PUCE) de una tienda online desarrollada con **Flask** y **PostgreSQL**.
Incluye catálogo de productos con herencia/POO (`Producto`, `ProductoFisico`,
`ProductoDigital`, `ProductoPerecible`), CRUD de productos, autenticación con
contraseñas encriptadas, roles y permisos (admin / cliente), carrito de compras,
subida de imágenes de producto y una interfaz responsive con Bootstrap.

## Requisitos previos

- Python 3.10+
- PostgreSQL instalado y en ejecución

## Instalación y ejecución

1. Clonar el repositorio y entrar a la carpeta del proyecto:

   ```bash
   git clone <URL_DEL_REPOSITORIO>
   cd tienda_online
   ```

2. Crear y activar un entorno virtual:

   ```bash
   python -m venv venv
   # Windows
   venv\Scripts\activate
   # macOS / Linux
   source venv/bin/activate
   ```

3. Instalar las dependencias:

   ```bash
   pip install -r requirements.txt
   ```

4. Crear la base de datos en PostgreSQL (usando `psql` o pgAdmin):

   ```sql
   CREATE DATABASE tienda_online;
   ```

5. Crear el archivo `.env` en la raíz del proyecto con tus propios datos
   (no se incluye en el repositorio por seguridad):

   ```env
   DB_USER=postgres
   DB_PASSWORD=tu_password
   DB_HOST=localhost
   DB_PORT=5432
   DB_NAME=tienda_online
   SECRET_KEY=un-texto-largo-y-aleatorio
   ```

6. Crear las tablas e insertar datos de prueba:

   ```bash
   python init_db.py
   ```

7. Ejecutar la aplicación:

   ```bash
   python app.py
   ```

8. Abrir en el navegador: [http://127.0.0.1:5000](http://127.0.0.1:5000)

## Credenciales de prueba

| Rol     | Correo              | Contraseña |
|---------|----------------------|------------|
| Admin   | admin@tienda.com     | admin123   |
| Cliente | cliente@tienda.com   | cliente123 |

## Funcionalidades principales

- Catálogo público de productos con precio calculado según el tipo (envío,
  licencia o descuento por vencimiento).
- Registro e inicio de sesión con contraseñas encriptadas (`werkzeug.security`).
- Roles y permisos: solo el **admin** puede crear, editar y desactivar
  productos; solo el **cliente** tiene acceso al carrito de compras.
- Subida de imágenes de producto (`static/uploads/`) al crear o editar un
  producto, con imagen por defecto cuando no se ha cargado ninguna.
- Carrito de compras funcional (agregar, quitar, ver total).
- Interfaz responsive con Bootstrap 5 e íconos de Bootstrap Icons.

## Capturas de pantalla

> Agrega aquí las capturas del catálogo, el detalle de producto y el carrito
> (por ejemplo dentro de una carpeta `docs/` del repositorio).

```
![Catálogo](docs/catalogo.png)
![Detalle de producto](docs/detalle.png)
![Carrito](docs/carrito.png)
```

## Estructura del proyecto

```
tienda_online/
├── app.py              # Rutas y lógica principal
├── auth.py              # Decoradores de autenticación y roles
├── config.py             # Configuración (BD, uploads, etc.)
├── init_db.py             # Script para crear tablas y datos de prueba
├── models.py               # Modelos (Usuario, Producto y subclases)
├── requirements.txt
├── templates/               # Plantillas Jinja2
└── static/
    ├── css/style.css          # Estilos propios
    ├── img/default.png          # Imagen por defecto
    └── uploads/                  # Imágenes subidas por el admin
```
