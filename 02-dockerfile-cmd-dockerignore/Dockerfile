FROM centos
LABEL version=1.0
LABEL description="This is an apache image"
LABEL vendor=yo
RUN yum install httpd -y
WORKDIR /var/www/html
COPY startbootstrap-freelancer-master .
ENV contenido prueba3
RUN echo "$contenido" > /var/www/html/prueba.html
RUN echo "$(whoami)" > /var/www/html/user.html
RUN useradd ricardo
USER ricardo
RUN echo "$(whoami)" > /tmp/user2.html
USER root
RUN cp /tmp/user2.html /var/www/html/user2.html
COPY run.sh /run.sh
CMD sh /run.sh
