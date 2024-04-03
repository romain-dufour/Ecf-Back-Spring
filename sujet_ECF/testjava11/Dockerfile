# Etape de build avec Maven
FROM maven:3.8.4-openjdk-11 AS builder
WORKDIR /app

# Copie du fichier pom.xml et téléchargement des dépendances
COPY pom.xml /app
RUN mvn dependency:go-offline

# Copie des fichiers sources et exécution de la construction
COPY src /app/src
RUN mvn package -DskipTests


FROM openjdk:11

WORKDIR /app

# Copie de l'artifact JAR depuis l'étape précédente
COPY --from=builder /app/target/testjava11-0.0.1-SNAPSHOT.jar /app/testjava11-0.0.1-SNAPSHOT.jar

# Exposition du port 8080
EXPOSE 8080

# Exécution de l'application Spring Boot
ENTRYPOINT ["java", "-jar", "testjava11-0.0.1-SNAPSHOT.jar"]


# <artifactId>back_employee</artifactId>
  #    <version>0.0.1-SNAPSHOT</version>