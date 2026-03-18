# Contenedores Docker - MySQL y MongoDB

Este proyecto contiene la configuración de dos contenedores Docker:
- **MySQL 8.0**
- **MongoDB (última versión)**

## Requisitos

- Docker instalado
- Docker Compose instalado

## Instrucciones de uso

### 1. Iniciar los contenedores

```bash
docker-compose up -d
```

El parámetro `-d` ejecuta los contenedores en segundo plano.

### 2. Verificar que los contenedores están corriendo

```bash
docker-compose ps
```

### 3. Acceder a los servicios

**MySQL:**
- Host: `localhost`
- Puerto: `3306`
- Usuario: `dbuser`
- Contraseña: `dbpassword`
- Base de datos: `mydb`

Conexión de ejemplo:
```bash
docker exec -it mysql_server mysql -u dbuser -p mydb
```

**MongoDB:**
- Host: `localhost`
- Puerto: `27017`
- Usuario: `admin`
- Contraseña: `mongopassword`
- Base de datos: `mydb`

Conexión de ejemplo:
```bash
docker exec -it mongo_server mongosh
```

### 4. Ver logs de los contenedores

```bash
docker-compose logs -f
```

### 5. Detener los contenedores

```bash
docker-compose stop
```

### 6. Eliminar los contenedores (conserva los datos)

```bash
docker-compose down
```

### 7. Eliminar todo (contenedores + volúmenes de datos)

```bash
docker-compose down -v
```

## Volúmenes persistentes

Los datos se guardan en volúmenes persistentes:
- `mysql_data`: Datos de MySQL
- `mongo_data`: Datos de MongoDB

Esto asegura que los datos persistan incluso si detienes los contenedores.

## Variables de entorno

Las variables sensibles están en el archivo `.env`. Puedes modificarlas según tus necesidades, pero recuerda cambiar las contraseñas por defecto en producción.

## Red interna

Los contenedores están conectados a una red llamada `databases` que les permite comunicarse entre sí usando sus nombres de servicio.
