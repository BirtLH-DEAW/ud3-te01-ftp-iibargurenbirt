FROM ubuntu:latest

RUN apt update && apt install -y proftpd

COPY ./proftpd.conf /etc/proftpd/proftpd.conf
COPY ./index.html /srv/ftp/
COPY ./css_index/ /srv/ftp/css_index/

ENTRYPOINT ["/bin/sh", "-c" , "service proftpd start && bash " ]

