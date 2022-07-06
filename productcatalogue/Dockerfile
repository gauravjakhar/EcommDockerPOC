#
# Build stage
#
FROM maven:3.6.0-jdk-11-slim AS build
COPY src /home/productcatalogue/src
COPY pom.xml /home/productcatalogue
RUN mvn -f /home/productcatalogue/pom.xml clean package

#
# Package stage
#
FROM openjdk:11-jre-slim
COPY --from=build /home/productcatalogue/target/productcatalogue-0.0.1-SNAPSHOT.jar /usr/local/lib/app.jar
ADD product-catalogue.yml app-config.yml
EXPOSE 8020
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/usr/local/lib/app.jar", "server", "app-config.yml"]

#ENTRYPOINT ["java","-jar","/usr/local/lib/app.jar"]


######### - default file added from git #####
#FROM openjdk:8-jre
#ADD target/productcatalogue-0.0.1-SNAPSHOT.jar app.jar
#ADD product-catalogue.yml app-config.yml
#EXPOSE 8020
#ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","app.jar", "server", "app-config.yml"]

#docker build -t productcatalogue . 
#docker run -dp 8010:8010 productcatalogue


#kubectl apply -f productcatalogue-service.yaml
