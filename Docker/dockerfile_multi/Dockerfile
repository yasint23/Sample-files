FROM nginx:latest
LABEL maintainer="Neco tomascerny2020@gmail.com"
ENV KULLANICI="Neco"
ARG COLOR 
RUN apt-get update -y && apt-get install -y wget curl htop
WORKDIR /gecici
ADD https://wordpress.org/latest.tar.gz .
WORKDIR /usr/share/nginx/html
COPY html/${COLOR} .
HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD curl -f http://localhost/ || exit 1
CMD ["./script.sh"]