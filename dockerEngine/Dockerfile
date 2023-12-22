FROM ubuntu:latest AS BUILD_IMAGE

RUN apt-get update && apt-get install -y wget unzip
RUN wget https://www.tooplate.com/zip-templates/2128_tween_agency.zip && unzip 2128_tween_agency.zip -d /root/app

FROM ubuntu:latest

LABEL "project"="devops"
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install apache2 -y
WORKDIR /var/www/html
RUN rm index.html
COPY --from=BUILD_IMAGE /root/app/* /var/www/html/
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
EXPOSE 80
VOLUME /var/log/apache2