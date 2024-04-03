FROM maven:3.8.4-openjdk-11 as builder

WORKDIR /app

COPY server/search-service/pom.xml .
RUN mvn dependency:go-offline

COPY server/search-service/src ./app/src
RUN mvn package -DskipTests

FROM openjdk:11

WORKDIR /app

# Copie de l'artifact JAR depuis l'étape précédente
COPY --from=builder /app/target/search-service-0.0.1-SNAPSHOT.jar /app/search-service-0.0.1-SNAPSHOT.jar

# Exposition du port 8080
EXPOSE 8080

# Exécution de l'application Spring Boot
ENTRYPOINT ["java", "-jar", "search-service-0.0.1-SNAPSHOT.jar"]


# <artifactId>search-service</artifactId>
  #    <version>0.0.1-SNAPSHOT</version>

