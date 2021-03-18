FROM gradle:jre8 as builder

COPY . /app
RUN ls -la /app
WORKDIR /app
RUN gradle bootJar

# Debug the build:
RUN ls -la /app/build/libs


FROM openjdk:8-jdk-alpine
VOLUME /myvolume

ARG TARGET=app/target
COPY --from=builder ${TARGET}/ /app/target/RestaurantList.jar

# Debug the build:
RUN ls -la /app/target


ENTRYPOINT ["java","-jar","./app/target/RestaurantList.jar"]
