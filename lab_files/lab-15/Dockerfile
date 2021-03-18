FROM gradle:jdk8 as builder

COPY . /app
RUN ls -la /app
WORKDIR /app
RUN gradle bootJar

# Debug the build:
RUN ls -la /app/build/libs


FROM openjdk:8-jdk-alpine
VOLUME /myvolume

ARG TARGET=app/build
COPY --from=builder ${TARGET}/ /app/build/RestaurantWeb.jar

# Debug the build:
RUN ls -la /app/build


ENTRYPOINT ["java","-jar","./app/build/RestaurantWeb.jar"]
