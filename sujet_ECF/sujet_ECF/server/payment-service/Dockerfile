FROM maven:3.6 as builder

WORKDIR /app

COPY server/payment-service/pom.xml /app
RUN mvn dependency:go-offline

COPY server/payment-service/src ./app/src
RUN mvn package -DskipTests

FROM openjdk:11

WORKDIR /app

# Copie de l'artifact JAR depuis l'étape précédente
COPY --from=builder /app/target/payment-service-0.0.1-SNAPSHOT.jar /app/payment-service-0.0.1-SNAPSHOT.jar

# Exposition du port 8080
EXPOSE 8080

# Exécution de l'application Spring Boot
ENTRYPOINT ["java", "-jar", "payment-service-0.0.1-SNAPSHOT.jar"]


# <artifactId>payment-service</artifactId>
  #    <version>0.0.1-SNAPSHOT</version>

