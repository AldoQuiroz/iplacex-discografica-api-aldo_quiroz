# Etapa 1: Compilación con Gradle y JDK 21
FROM gradle:8.14.3-jdk21 AS build
WORKDIR /app

# Copiamos todo el proyecto al contenedor
COPY . .

# Ejecutamos el build usando bootJar (Spring Boot)
RUN gradle bootJar --no-daemon

# Etapa 2: Ejecución con OpenJDK 21
FROM eclipse-temurin:21-jre AS run
WORKDIR /app

# Copiamos el .jar generado desde la etapa anterior
COPY --from=build /app/build/libs/*.jar app.jar

# Ejecutamos el archivo .jar
ENTRYPOINT ["java", "-jar", "app.jar"]