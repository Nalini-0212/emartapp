FROM eclipse-temurin:8-jdk AS build
WORKDIR /usr/src/app
COPY . ./new
RUN apt-get update && apt-get install -y maven
RUN cd new && mvn clean install -DskipTests

FROM eclipse-temurin:8-jdk
WORKDIR /usr/src/app
COPY --from=build /usr/src/app/new/target/book-work-0.0.1-SNAPSHOT.jar ./book-work-0.0.1-SNAPSHOT.jar
ENTRYPOINT ["java","-jar","book-work-0.0.1-SNAPSHOT.jar"]
EXPOSE 9090
