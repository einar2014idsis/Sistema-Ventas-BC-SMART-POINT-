# BC Smart Point | Sistema de ventas

Aplicación web de comercio construida con ASP.NET Core MVC y SQL Server. El repositorio es un **fork**; conserva la atribución del proyecto original y distingue las contribuciones propias al presentarlo en un portafolio.

## Funcionalidades

- Catálogo de productos y categorías, registro e inicio de sesión.
- Carrito almacenado en sesión, validación de disponibilidad y proceso de checkout.
- Cupones con validación de vigencia, cálculo de importes e impuesto.
- Registro transaccional de venta, detalle, descuento de stock y creación de envío.
- Pago por transferencia con carga de comprobante, confirmación y consulta de pedidos.
- Panel administrativo para categorías, proveedores y productos.

El flujo registra estados y comprobantes; no debe interpretarse como verificación automática de transferencias bancarias.

## Tecnologías y arquitectura

C#, ASP.NET Core MVC 8, Razor, Entity Framework Core 8, SQL Server, autenticación por cookies, sesión y BCrypt. Los controladores están en `SistemaBCSmartPoint/Controllers/`; `Services/` contiene lógica de autenticación, carrito y ventas; `Data/` agrupa el contexto; `Models/` y `Views/` contienen entidades, modelos de pantalla y vistas. El dominio incluye usuarios, clientes, productos, categorías, proveedores, ventas, detalles, cupones y envíos. `TestProject1/` contiene pruebas MSTest de modelos.

## Ejecución

Instala .NET 8 SDK y SQL Server. Configura la cadena `ConnectionStrings:StringSQL` mediante secretos locales o variables de entorno, prepara el esquema de base de datos compatible con el modelo y ejecuta:

```bash
dotnet restore SistemaBCSmartPoint/Sistema_BC_SMART_POINT.csproj
dotnet run --project SistemaBCSmartPoint/Sistema_BC_SMART_POINT.csproj
```

Consulta `Properties/launchSettings.json` para los perfiles. La configuración de pago y las credenciales deben revisarse localmente; no publiques secretos ni comprobantes reales. Para ejecutar las pruebas disponibles usa `dotnet test TestProject1/TestProject1.csproj`.
