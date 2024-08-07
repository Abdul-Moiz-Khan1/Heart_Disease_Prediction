# Stage 1: Build the application
FROM gradle:7.2-jdk11 AS build

# Copy the project files to the container
COPY --chown=gradle:gradle . /home/gradle/project

# Set the working directory
WORKDIR /home/gradle/project

# Build the application
RUN gradle build

# Stage 2: Run the application
FROM openjdk:11-jre-slim

# Copy the built JAR file from the build stage
COPY --from=build /home/gradle/project/build/libs/*.jar /app/your-app-name.jar

# Set the working directory
WORKDIR /app

# Specify the command to run the application
CMD ["java", "-jar", "com.example.heart_disease.jar"]
