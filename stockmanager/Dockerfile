#
# Build stage
#
FROM maven:3.6.0-jdk-11-slim AS build
COPY src /home/stockmanager/src
COPY pom.xml /home/stockmanager
RUN mvn -f /home/stockmanager/pom.xml clean package

#
# Package stage
#
FROM openjdk:11-jre-slim
COPY --from=build /home/stockmanager/target/stockmanager-0.0.1-SNAPSHOT.jar /usr/local/lib/app.jar
EXPOSE 8030
ENTRYPOINT ["java","-jar","/usr/local/lib/app.jar"]


######### - default file added from git #####
#FROM openjdk:8-jre
#ADD target/stockmanager-0.0.1-SNAPSHOT.jar app.jar
#EXPOSE 8030
#ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]


#docker build -t stockmanager . 
#docker run -dp 8010:8010 stockmanager


#kubectl apply -f stockmanager-service.yaml
