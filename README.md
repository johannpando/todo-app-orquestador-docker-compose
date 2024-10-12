# Orquestador de Servicios - Docker Compose

Este proyecto incluye un **backend** desarrollado con **Spring Boot**, un **frontend** en **React**, y una base de datos **PostgreSQL**. Los tres servicios se orquestan mediante **Docker Compose**. A continuación se detalla la estructura de carpetas del proyecto, la configuración de los servicios, red, volúmenes y la base de datos.

## Estructura del Proyecto# Orquestador de Servicios - Docker Compose

Este proyecto incluye un **backend** desarrollado en **Spring Boot**, un **frontend** en **React**, y una base de datos **PostgreSQL**, todo orquestado con **Docker Compose**. A continuación, se detalla la estructura del proyecto, configuración de los servicios, red, volúmenes y base de datos. La estructura de carpetas del proyecto es la siguiente: `todo-app/` contiene el archivo `docker-compose.yml`, mientras que `todo-app-springboot/` es el directorio del backend y `todo-app-react/` es el directorio del frontend. Todos estos directorios están en el mismo nivel. En el archivo `docker-compose.yml`, los servicios se definen de la siguiente manera: el servicio **backend** usa la imagen de Spring Boot construida a partir de su Dockerfile en `todo-app-springboot/`, el servicio **frontend** utiliza una imagen de React construida a partir del Dockerfile en `todo-app-react/`, y el servicio **postgres** utiliza la imagen oficial de PostgreSQL. Los tres servicios están conectados a una misma red llamada `todo-network`, y se definen volúmenes persistentes para la base de datos PostgreSQL, asegurando que los datos se conserven entre reinicios del contenedor. El contenido del archivo `docker-compose.yml` es el siguiente:

```yaml
version: '3.8'
services:
  backend:
    image: todo-app-springboot
    build:
      context: ../todo-app-springboot
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    networks:
      - todo-network
    depends_on:
      - postgres

  frontend:
    image: todo-app-react
    build:
      context: ../todo-app-react
      dockerfile: Dockerfile
    ports:
      - "3001:80"
    networks:
      - todo-network

  postgres:
    image: postgres:latest
    environment:
      POSTGRES_DB: mi_base_de_datos
      POSTGRES_USER: mi_usuario
      POSTGRES_PASSWORD: mi_contraseña
    ports:
      - "5432:5432"
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - todo-network

networks:
  todo-network:
    driver: bridge

volumes:
  db-data:# Orquestador de Servicios - Docker Compose

Este proyecto incluye un **backend** desarrollado en **Spring Boot**, un **frontend** en **React**, y una base de datos **PostgreSQL**, todo orquestado con **Docker Compose**. A continuación, se detalla la estructura del proyecto, configuración de los servicios, red, volúmenes y base de datos. La estructura de carpetas del proyecto es la siguiente: `todo-app/` contiene el archivo `docker-compose.yml`, mientras que `todo-app-springboot/` es el directorio del backend y `todo-app-react/` es el directorio del frontend. Todos estos directorios están en el mismo nivel. En el archivo `docker-compose.yml`, los servicios se definen de la siguiente manera: el servicio **backend** usa la imagen de Spring Boot construida a partir de su Dockerfile en `todo-app-springboot/`, el servicio **frontend** utiliza una imagen de React construida a partir del Dockerfile en `todo-app-react/`, y el servicio **postgres** utiliza la imagen oficial de PostgreSQL. Los tres servicios están conectados a una misma red llamada `todo-network`, y se definen volúmenes persistentes para la base de datos PostgreSQL, asegurando que los datos se conserven entre reinicios del contenedor. El contenido del archivo `docker-compose.yml` es el siguiente:

```yaml
version: '3.8'
services:
  backend:
    image: todo-app-springboot
    build:
      context: ../todo-app-springboot
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    networks:
      - todo-network
    depends_on:
      - postgres

  frontend:
    image: todo-app-react
    build:
      context: ../todo-app-react
      dockerfile: Dockerfile
    ports:
      - "3001:80"
    networks:
      - todo-network

  postgres:
    image: postgres:latest
    environment:
      POSTGRES_DB: mi_base_de_datos
      POSTGRES_USER: mi_usuario
      POSTGRES_PASSWORD: mi_contraseña
    ports:
      - "5432:5432"
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - todo-network

networks:
  todo-network:
    driver: bridge

volumes:
  db-data:

La estructura del proyecto es la siguiente:

todo-app/
│
├── docker-compose.yml  # Archivo de configuración para Docker Compose
│
├── todo-app-springboot/  # Directorio del backend con Spring Boot
│   └── (Archivos del proyecto backend)
│
├── todo-app-react/  # Directorio del frontend con React
│   └── (Archivos del proyecto frontend)

# Orquestador de Servicios - Docker Compose

Este proyecto incluye un **backend** desarrollado en **Spring Boot**, un **frontend** en **React**, y una base de datos **PostgreSQL**, todo orquestado con **Docker Compose**. A continuación, se detalla la estructura del proyecto, configuración de los servicios, red, volúmenes y base de datos. La estructura de carpetas del proyecto es la siguiente: `todo-app/` contiene el archivo `docker-compose.yml`, mientras que `todo-app-springboot/` es el directorio del backend y `todo-app-react/` es el directorio del frontend. Todos estos directorios están en el mismo nivel. En el archivo `docker-compose.yml`, los servicios se definen de la siguiente manera: el servicio **backend** usa la imagen de Spring Boot construida a partir de su Dockerfile en `todo-app-springboot/`, el servicio **frontend** utiliza una imagen de React construida a partir del Dockerfile en `todo-app-react/`, y el servicio **postgres** utiliza la imagen oficial de PostgreSQL. Los tres servicios están conectados a una misma red llamada `todo-network`, y se definen volúmenes persistentes para la base de datos PostgreSQL, asegurando que los datos se conserven entre reinicios del contenedor. El contenido del archivo `docker-compose.yml` es el siguiente:

```yaml
version: '3.8'
services:
  backend:
    image: todo-app-springboot
    build:
      context: ../todo-app-springboot
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    networks:
      - todo-network
    depends_on:
      - postgres

  frontend:
    image: todo-app-react
    build:
      context: ../todo-app-react
      dockerfile: Dockerfile
    ports:
      - "3001:80"
    networks:
      - todo-network

  postgres:
    image: postgres:latest
    environment:
      POSTGRES_DB: mi_base_de_datos
      POSTGRES_USER: mi_usuario
      POSTGRES_PASSWORD: mi_contraseña
    ports:
      - "5432:5432"
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - todo-network

networks:
  todo-network:
    driver: bridge

volumes:
  db-data: