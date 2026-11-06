
# Deployment Guide

## 1. Crear la instancia EC2

- Crear una instancia Amazon EC2.
- Seleccionar Ubuntu Server.
- Configurar el acceso SSH.
- Asignar una dirección IPv4 pública.
- Configurar las reglas de entrada del Security Group.

Puertos utilizados:

| Puerto | Protocolo | Uso |
|---|---|---|
| 22 | TCP | SSH |
| 80 | TCP | HTTP |
| 443 | TCP | HTTPS |

## 2. Instalar Nginx

```bash
sudo apt update
sudo apt install nginx -y
```

Verificar el servicio:

```bash
sudo systemctl status nginx
```

## 3. Configurar los sitios web

Crear los directorios:

```bash
sudo mkdir -p /var/www/app
sudo mkdir -p /var/www/web
```

Copiar los archivos HTML a sus respectivos directorios.

Configurar los virtual hosts en:

```text
/etc/nginx/sites-available/
```

Habilitar las configuraciones mediante enlaces simbólicos en:

```text
/etc/nginx/sites-enabled/
```

Validar y recargar Nginx:

```bash
sudo nginx -t
sudo systemctl reload nginx
```

## 4. Configurar DNS con Amazon Route 53

Crear registros tipo A para asociar los subdominios con la dirección IPv4 pública de la instancia EC2.

Verificar la resolución DNS:

```bash
nslookup app.example.com
nslookup web.example.com
```

## 5. Configurar HTTPS

Instalar Certbot y su complemento para Nginx:

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Solicitar el certificado:

```bash
sudo certbot --nginx -d app.example.com -d web.example.com
```

Verificar los certificados:

```bash
sudo certbot certificates
```

## 6. Verificar el despliegue

Comprobar el estado de Nginx:

```bash
sudo systemctl status nginx
```

Validar la configuración:

```bash
sudo nginx -t
```

Finalmente, acceder a los subdominios mediante HTTPS para comprobar que cada uno muestra su sitio web correspondiente.

**Nota:** Los dominios `example.com` son valores de ejemplo. Deben reemplazarse por los dominios configurados en Route 53.
