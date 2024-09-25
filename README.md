# micro-blog-deploy

Repositorio orientado al despliegue del proyecto micro blog haciendo uso de
`codespaces`

## Setup

Crear archivo `.env` con las siguientes variables. Recuerde modificar los valores
según correspondan a su entorno y servicios.

```ini
MONGO_ROOT_USER=
MONGO_ROOT_PASSWORD=

MONGO_URI="mongodb://${MONGO_ROOT_USER}:${MONGO_ROOT_PASSWORD}@mongodb:27017/micro-blog?authSource=admin"
JWT_SECRET_KEY=
```

## Deploy

```bash
# clonar repositorios del proyecto
git clone https://gitlab.com/cymetria-2024/micro-blog.git
git clone https://gitlab.com/cymetria-2024/micro-blog-front.git

# construir front-end
cd micro-blog-front
yarn
yarn build

cd ..

# descargar imágenes docker
docker compose pull

# construir imagen del back-end
docker compose build

# desplegar con docker compose
docker compose up -d
```

## Instalar Nginx (Ubuntu)

```bash
# actualizar listado de paquetes
sudo apt update

# actualizar sistema operativo
sudo apt full-upgrade -y

# limpieza de paquetes no usados y cache
sudo apt autoremove -y
sudo apt clean -y

# installar nginx
sudo apt install nginx-extras

# iniciar el servicio nginx (codespaces)
sudo service nginx start

# iniciar el servicio nginx (server, vps, etc)
sudo systemctl enable --now nginx
```

Use el archivo `default` adjunto en este proyecto como referencia para la creación de las rutas en el servidor nginx. Este archivo se encuentra normalmente en la ruta `/etc/nginx/sites-available/default`

```bash
# reiniciar nginx (en caliente)
sudo nginx -s reload
```
