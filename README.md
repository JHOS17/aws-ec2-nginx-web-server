
# AWS EC2 Web Server with Nginx

Proyecto práctico de despliegue y configuración de dos sitios web en una instancia Amazon EC2 utilizando Ubuntu Server, Nginx, Amazon Route 53 y certificados SSL/TLS mediante Let's Encrypt.

## Descripción

El objetivo del proyecto fue implementar un servidor web en AWS capaz de alojar dos sitios independientes mediante subdominios personalizados.

Se configuraron virtual hosts en Nginx para dirigir las solicitudes HTTP/HTTPS hacia diferentes directorios, además de configurar la resolución DNS y la protección de las conexiones mediante HTTPS.

## Arquitectura

```text
                    Internet
                       |
                 Amazon Route 53
                  DNS / Subdomains
                       |
                  Amazon EC2
                  Ubuntu Server
                       |
                     Nginx
                       |
              +--------+--------+
              |                 |
          Subdominio APP    Subdominio WEB
              |                 |
          /var/www/app      /var/www/web
              |                 |
          index.html        index.html
              |                 |
              +--------+--------+
                       |
               HTTPS / SSL-TLS
               Let's Encrypt
                   Certbot
```

## Tecnologías utilizadas

- **AWS EC2:** infraestructura de cómputo en la nube.
- **Ubuntu Server:** sistema operativo del servidor.
- **Nginx:** servidor web y configuración de virtual hosts.
- **Amazon Route 53:** gestión de DNS y subdominios.
- **Let's Encrypt:** emisión de certificados SSL/TLS.
- **Certbot:** automatización de la configuración HTTPS.
- **HTML, CSS y JavaScript:** desarrollo de las páginas web.

## Funcionalidades implementadas

- Despliegue de una instancia EC2 con Ubuntu.
- Instalación y configuración de Nginx.
- Configuración de dos sitios web independientes.
- Creación de virtual hosts mediante `sites-available` y `sites-enabled`.
- Configuración de registros DNS tipo A en Route 53.
- Configuración de subdominios personalizados.
- Implementación de HTTPS mediante certificados de Let's Encrypt.
- Redirección del tráfico HTTP hacia HTTPS.
- Verificación del funcionamiento de los sitios web.

## Estructura del repositorio

```text
aws-ec2-nginx-web-server/
├── nginx/
│   ├── app.conf
│   └── web.conf
├── website/
│   ├── app/
│   │   └── index.html
│   └── web/
│       └── index.html
├── screenshots/
├── docs/
│   └── deployment.md
└── README.md
```

## Evidencias

Las capturas de pantalla del despliegue, configuración DNS, servidor Nginx y sitios web se encuentran en el directorio `/Capturas-AWS`.

## Seguridad

- Uso de HTTPS mediante certificados SSL/TLS.
- Configuración de reglas de acceso mediante Security Groups.
- No se incluyen claves privadas, credenciales AWS ni certificados privados en el repositorio.

## Autor

**Jhosep Orozco**

Estudiante de Ingeniería de Sistemas e Inteligencia Artificial.

GitHub: https://github.com/JHOS17

---

Proyecto desarrollado con fines de aprendizaje práctico en Cloud Computing y administración de servidores Linux.
