# P2 · API REST de productos

**Equipo:** Vera Guillen Diana #232310227 & Arguijo Vazquez Cristoper Daniel #232310075  
**Materia:** Programación Web · Grupo 4X7B · Unidad 5

## Descripción
Servicio web hecho con Node.js y Express que administra productos (CRUD) en memoria.
Responde en JSON y usa los códigos de estado HTTP correspondientes.

## Instalación
```bash
npm install
npm start          # http://localhost:3000
# o, con recarga automática:
npm run dev
```
Requiere Node.js 18 o superior.

## Contrato de la API
| Método | Ruta | Acción | Respuesta correcta | Posibles errores |
|--------|------|--------|--------------------|------------------|
| GET | /api/productos | Listar todos | 200 + arreglo | — |
| GET | /api/productos/:id | Ver uno | 200 + objeto | 404 |
| POST | /api/productos | Crear | 201 + objeto creado | 400 |
| PUT | /api/productos/:id | Actualizar | 200 + objeto actualizado | 400, 404 |
| DELETE | /api/productos/:id | Eliminar | 204 sin contenido | 404 |

Extra: `GET /api/productos?buscar=tec` filtra por nombre.

## Modelo de producto
```json
{ "id": 1, "nombre": "Teclado", "precio": 350, "stock": 10 }
```
Validaciones: `nombre` texto obligatorio, `precio` número ≥ 0, `stock` entero ≥ 0.

## Ejemplo
**Petición**
```http
POST /api/productos
Content-Type: application/json

{ "nombre": "Monitor", "precio": 2500, "stock": 5 }
```
**Respuesta `201 Created`**
```json
{ "id": 3, "nombre": "Monitor", "precio": 2500, "stock": 5 }
```
**Petición inválida** `{"nombre":"","precio":-1}` → **`400 Bad Request`**
```json
{ "errores": ["nombre es obligatorio", "precio debe ser un número positivo", "stock debe ser un entero positivo"] }
```

## Pruebas
Importar `P2_Productos.postman_collection.json` en Postman (8 peticiones).
