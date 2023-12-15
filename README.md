\
README para el Proyecto del Portafolio Web
============================================

Descripción General
-------------------

Este proyecto es para un portafolio web alojado en Kubernetes. Utiliza GitHub Actions para la integración y despliegue continuos, subiendo el código compilado a Docker Hub y luego implementándolo en un clúster de Kubernetes. La configuración asegura que la aplicación sea accesible y segura, utilizando un certificado TLS proporcionado por Let's Encrypt.

Arquitectura
------------

-   Código Fuente: El código de la página está alojado en GitHub.
-   CI/CD: GitHub Actions se utiliza para la compilación y despliegue.
-   Contenedorización: La imagen compilada se sube a Docker Hub.
-   Despliegue en Kubernetes: La imagen se implementa en un clúster de Kubernetes.

Componentes de Kubernetes
-------------------------

1.  Deployment: `mi-portfolio`

    -   Replicas: 4
    -   Contenedor: `portfolio-container`
    -   Imagen: `alvarosg97/portfolio:1702628528`
    -   Puerto: 80
2.  Service: `mi-portfolio-svc`

    -   Tipo: ClusterIP
    -   Puerto: 80
3.  Ingress: `mi-portfolio-ingress`

    -   TLS: Habilitado con Let's Encrypt
    -   Host: `asanchez.orsatecsl.es`
4.  ClusterIssuer: `letsencrypt-prod`

    -   ACME Server: Let's Encrypt
    -   Email: `alvarosanchezgon1997@gmail.com`

Proceso de CI/CD con GitHub Actions
-----------------------------------

El proceso de integración y despliegue continuo se realiza mediante GitHub Actions. Este proceso incluye:

-   Compilación del código fuente.
-   Construcción de la imagen del contenedor.
-   Subida de la imagen al repositorio de Docker Hub.
-   Despliegue automático en el clúster de Kubernetes.

Seguridad y Certificados
------------------------

El sitio web está asegurado utilizando un certificado TLS emitido por Let's Encrypt, que se gestiona automáticamente a través de Cert-Manager en Kubernetes.