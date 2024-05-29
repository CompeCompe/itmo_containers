FROM openjdk:21
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app


COPY package.json /usr/src/app
RUN cat package.json && echo "read package.json"

COPY card-service-1.0.jar /usr/src/app

VOLUME /usr/src/app

ENTRYPOINT ["java", "-jar", "-Dserver.port=8888", "/usr/src/app/card-service-1.0.jar"]

