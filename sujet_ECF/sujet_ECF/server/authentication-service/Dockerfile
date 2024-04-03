FROM maven:3.8.4-openjdk-11 as builder

WORKDIR /app

COPY pom.xml /app
RUN mvn dependency:go-offline

COPY src ./app/src
RUN mvn package -DskipTests

# Étape de repackage avec le plugin Spring Boot
RUN mvn org.springframework.boot:spring-boot-maven-plugin:2.5.5:repackage -DskipTests

FROM openjdk:11

WORKDIR /app

# Copie de l'artifact JAR depuis l'étape précédente
COPY --from=builder /app/target/authentication-service-0.0.1-SNAPSHOT.jar /app/authentication-service-0.0.1-SNAPSHOT.jar

# Exposition du port 8080
EXPOSE 8080

# Exécution de l'application Spring Boot
ENTRYPOINT ["java", "-jar", "authentication-service-0.0.1-SNAPSHOT.jar"]


# <artifactId>authentication-service</artifactId>
  #    <version>0.0.1-SNAPSHOT</version>

