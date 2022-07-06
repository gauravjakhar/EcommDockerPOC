#
# Build stage
#
FROM maven:3.6.0-jdk-11-slim AS build
COPY src /home/shopfront/src
COPY pom.xml /home/shopfront
RUN mvn -f /home/shopfront/pom.xml clean package

#
# Package stage
#
FROM openjdk:11-jre-slim
COPY --from=build /home/shopfront/target/shopfront-0.0.1-SNAPSHOT.jar /usr/local/lib/app.jar
EXPOSE 8010
ENTRYPOINT ["java","-jar","/usr/local/lib/app.jar"]


######### - default file added from git #####
#FROM openjdk:8-jre
#ADD target/shopfront-0.0.1-SNAPSHOT.jar app.jar
#EXPOSE 8010
#ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]



#docker build -t shopfront . 
#docker run -dp 8010:8010 shopfront


#kubectl apply -f shopfront-service.yaml
