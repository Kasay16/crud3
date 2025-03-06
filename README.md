# crud3
 crud3
# 1 
crear proyecto web c#
aplicacionweb asp.netcore
# 2
tool
administrador de paquetes nuget
entityframework sql y tool
# 3
tablas

CREATE TABLE Usuarios (
    id UNIQUEIDENTIFIER PRIMARY KEY,  -- ID manual, no autoincrementable
    nombre VARCHAR(100) NOT NULL,
    correo VARCHAR(100) UNIQUE NOT NULL,
    telefono VARCHAR(20) NOT NULL
);itulo VARCHAR(200) NOT NULL,
    autor VARCHAR(100) NOT NULL,
    anio_publicacion INT NOT NULL
);

CREAT

CREATE TABLE Libros (
    id UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(), -- ID manual pero con valor por defecto
    tE TABLE Prestamos (
    id UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(),  -- ID manual pero con valor por defecto
    uFOREIGN KEY (usuario_id) REFERENCES Usuarios(id),
    FOREIGN KEY (libro_id) REFERENCES Libros(id)
);suario_id UNIQUEIDENTIFIER NOT NULL,
    libro_id UNIQUEIDENTIFIER NOT NULL,
    fecha_prestamo DATE NOT NULL,
    fecha_devolucion DATE NULL,
    -- Crear la base de datos
CREATE DATABASE BibliotecaDB;
GO

-- Usar la base de datos recién creada
USE BibliotecaDB;
GO

-- Crear la tabla de Usuarios
CREATE TABLE Usuarios (
    id UNIQUEIDENTIFIER PRIMARY KEY,  -- ID manual, no autoincrementable
    nombre VARCHAR(100) NOT NULL,
    correo VARCHAR(100) UNIQUE NOT NULL,
    telefono VARCHAR(20) NOT NULL
);
GO

-- Crear la tabla de Libros
CREATE TABLE Libros (
    id UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(), -- ID manual pero con valor por defecto
    titulo VARCHAR(200) NOT NULL,
    autor VARCHAR(100) NOT NULL,
    anio_publicacion INT NOT NULL
);
GO

-- Crear la tabla de Prestamos
CREATE TABLE Prestamos (
    id UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(),  -- ID manual pero con valor por defecto
    usuario_id UNIQUEIDENTIFIER NOT NULL,
    libro_id UNIQUEIDENTIFIER NOT NULL,
    fecha_prestamo DATE NOT NULL,
    fecha_devolucion DATE NULL,
    FOREIGN KEY (usuario_id) REFERENCES Usuarios(id),
    FOREIGN KEY (libro_id) REFERENCES Libros(id)
);
GO
# consola nuget para comando

Scaffold-DbContext "Server=LAPTOP-PNG8B978\SQLEXPRESS;Database=BibliotecaBD;Integrated Security=True;TrustServerCertificate=True;Encrypt=False" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models
# controller agregar controlador
entityframework

# dir shared 
luego layaout

# asp-controller

asp-controller="nombre controlador" asp-action="vista"

# luego en index.cs

añadir clases btn btn-warning

# configurar

db DbContext
using MVCCRUD2.Models; // Asegúrate de importar el namespace correcto

var builder = WebApplication.CreateBuilder(args);

// Configurar la conexión a la base de datos
builder.Services.AddDbContext<BibliotecaDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));

// Agregar servicios al contenedor
builder.Services.AddControllersWithViews();

var app = builder.Build();

# buscar

public async Task<IActionResult> Index(string buscar)
        {
            var usuarios = _context.Usuarios.AsQueryable(); // Asegurar que sea una consulta

            if (!string.IsNullOrEmpty(buscar))
            {
                usuarios = usuarios.Where(s => s.Nombre!.Contains(buscar));
            }

            return View(await usuarios.ToListAsync()); // Aquí aplicamos ToListAsync sobre la consulta filtrada
        }

