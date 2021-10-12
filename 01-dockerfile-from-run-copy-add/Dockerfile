FROM centos
RUN yum install httpd -y
WORKDIR /var/www/html
COPY startbootstrap-freelancer-master .
ENV contenido prueba3
RUN echo "$contenido" > /var/www/html/prueba.html
EXPOSE 81
CMD apachectl -DFOREGROUND
