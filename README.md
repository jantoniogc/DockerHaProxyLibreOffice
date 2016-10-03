# DockerImages
## Construccion de la imagen jantoniogc/libreoffice

1) Descargar el proyecto “DockerImages”.

2) Ubicarse en la carpeta “jantoniogc-libreoffice”

3) Construir la imagen:
  - $ docker build -t jantoniogc/libreoffice .

## Construccion de la imagen jantoniogc/haproxy
1) Descargar el proyecto “DockerImages” del CVS.

2) Ubicarse en la carpeta “jantoniogc-haproxy”

3) Construir la imagen
  - $ docker build -t jantoniogc/haproxy .

## Construccion de la imagen jantoniogc/haproxy
1) Descargar el proyecto “DockerImages” del CVS.

2) Ubicarse en la carpeta “inta-haproxy”

3) Construir la imagen

  - $ docker build -t jantoniogc/haproxy .

4) Crear la carpeta “/etc/haproxy”:
  - $ mkdir -p /etc/haproxyCopiar los siguientes ficheros en “/etc/haproxy”:
  - $ cp haproxy.cfg /etc/haproxy
  - $ cp haproxy_default.cfg /etc/haproxy
  - $ cp reload.sh /etc/haproxy

## Ejecución de los contenedores
1) Nos situamos en la raiz del proyecto

2) Ejecutamos
  - $ docker-compose up -d

  Esto crea los conectados y listos para funcionar.

3) Si se desean más instancias (o menos) de LibreOffice, hay que ejecutar:
  - $ docker-compose scale libreoffice=<N>
