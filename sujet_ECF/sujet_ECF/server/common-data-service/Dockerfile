FROM maven:3.8.4-openjdk-11 as builder

WORKDIR /app

COPY server/common-data-service/pom.xml /app
RUN mvn dependency:go-offline

COPY server/common-data-service/src ./app/src
RUN mvn package -DskipTests

FROM openjdk:11

WORKDIR /app

COPY --from=builder /app/target/common-data-service-0.0.1-SNAPSHOT.jar /app/common-data-service-0.0.1-SNAPSHOT.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "common-data-service-0.0.1-SNAPSHOT.jar"]


# <artifactId>common-data-service</artifactId>
  #    <version>0.0.1-SNAPSHOT</version>

