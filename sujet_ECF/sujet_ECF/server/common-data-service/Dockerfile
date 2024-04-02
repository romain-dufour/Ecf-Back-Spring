FROM maven:3.6 as builder

WORKDIR /app

COPY common-data-service/pom.xml .
RUN mvn dependency:go-offline

COPY common-data-service/src ./src
RUN mvn package -DskipTests

FROM openjdk:11

WORKDIR /app

COPY --from=builder /app/target/common-data-service-0.0.1-SNAPSHOT.jar .

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "common-data-service-0.0.1-SNAPSHOT.jar"]


# <artifactId>common-data-service</artifactId>
  #    <version>0.0.1-SNAPSHOT</version>

