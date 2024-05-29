FROM openjdk:21
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
ENTRYPOINT ["java", "-jar", "-Dserver.port=8888", "/usr/src/app/card-service-1.0.jar"]

COPY package.json /usr/src/app
RUN cat package.json
RUN echo "read package.json"
COPY . /usr/src/app
VOLUME /usr/src/app
