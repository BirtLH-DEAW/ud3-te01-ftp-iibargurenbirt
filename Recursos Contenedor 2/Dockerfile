FROM ubuntu:latest

RUN apt update && apt install -y proftpd proftpd-mod-crypto

RUN mkdir -p /etc/ssl/private
RUN mkdir -p /etc/ssl/certs

COPY ./proftpd.key /etc/ssl/private/
COPY ./proftpd.crt /etc/ssl/certs/

COPY ./proftpd.conf /etc/proftpd/
COPY ./modules.conf /etc/proftpd/
COPY ./tls.conf /etc/proftpd/

COPY DefaultRoot_comandos.txt /srv/deaw/
COPY FTP_comandos.txt /srv/deaw/
COPY FTPanonimo_comandos.txt /srv/deaw/
COPY README.txt /srv/deaw/

RUN groupadd deaw
RUN useradd deaw -p deaw -c -m -d /srv/deaw -s /sbin/nologin -g deaw
#RUN echo -e "deaw\ndeaw" | passwd deaw
RUN echo "deaw:deaw" | chpasswd
RUN chown -R deaw /srv/deaw/
RUN chmod -R u+w /srv/deaw/

ENTRYPOINT ["/bin/sh", "-c" , "service proftpd start && bash " ]
