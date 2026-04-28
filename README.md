# Taller AWS: Web estática en S3 y CloudFront

En este taller vas a subir una web estática (HTML y CSS) a **Amazon S3** y la expondrás a Internet mediante **Amazon CloudFront**, la red de entrega de contenido (CDN) de AWS.

## Requisitos previos

- Cuenta de AWS con permisos para usar S3 y CloudFront.
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) instalado y configurado (`aws configure`) con credenciales válidas.
- [Git](https://git-scm.com/) instalado.

> **Nombre del bucket:** Los nombres de bucket S3 son únicos en toda AWS. Si `static-web-restaurant` ya está en uso, sustituye `static-web-restaurant` por otro nombre (por ejemplo `static-web-restaurant-tu-iniciales`) en **todos** los comandos siguientes.

## Paso 1: Crear el bucket S3

```bash
aws s3 mb s3://static-web-restaurant
```

## Paso 2: Clonar el repositorio del taller

```bash
git clone https://github.com/iovanic/aws_workshop_static_web.git
```

## Paso 3: Subir los archivos al bucket

Este comando copia el contenido del proyecto al bucket y **excluye** la carpeta `.git` para no subir el historial de Git.

```bash
aws s3 cp aws_workshop_static_web/ s3://static-web-restaurant/ --recursive --exclude ".git/*"
```

## Paso 4: Comprobar que los objetos están en S3

```bash
aws s3 ls s3://static-web-restaurant/
```

Deberías ver al menos `index.html` y `styles.css` (u otros archivos del sitio).

## Resumen

| Recurso    | Rol |
|-----------|-----|
| **S3**    | Almacena los archivos estáticos del sitio. |
| **CloudFront** | Entrega el contenido por HTTPS con baja latencia y caché en el edge. |

Si tenéis problemas con permisos, región o nombre de bucket, consultad con el instructor.
