# Use an official OpenJDK runtime as a parent image
FROM openjdk:17-jdk-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the Maven wrapper and pom.xml file from the backend folder
COPY backend/.mvn/ .mvn
COPY backend/mvnw backend/pom.xml ./

# Download dependencies
RUN ./mvnw dependency:go-offline

# Copy the rest of your application's source code from the backend folder
COPY backend/src ./src

# Compile and package the application into a .jar file
RUN ./mvnw package -DskipTests

# Expose the port your app runs on (Spring Boot default is 8080)
EXPOSE 8080

# The command to run your application
ENTRYPOINT ["java", "-jar", "target/projectmanagement-0.0.1-SNAPSHOT.jar"]