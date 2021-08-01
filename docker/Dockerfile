FROM debian:stretch

ENV API_UMBRELLA_VERSION 0.15.1-1~stretch

USER 0
RUN apt-get update -y 
RUN apt-get install -y gnupg2
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 367404D553B42995

# Install API Umbrella
RUN echo "deb http://dl.bintray.com/nrel/api-umbrella-debian stretch main" >> /etc/apt/sources.list.d/api-umbrella.list
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -y --no-install-recommends --allow-unauthenticated install api-umbrella

# Define mountable directories
VOLUME ["/etc/api-umbrella", "/opt/api-umbrella/var/db", "/opt/api-umbrella/var/log"]

USER 1001

# Expose HTTP and HTTPS ports
EXPOSE 8080 8443

# Run the API Umbrella service
CMD ["api-umbrella", "run"]
