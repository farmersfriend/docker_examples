FROM clojure:openjdk-11-lein-2.9.3-buster

WORKDIR /app

# Dependencies
COPY project.clj .
RUN ["lein", "deps"]

# Copy the actual code and generate the uberjar
COPY . /app
RUN ["lein", "uberjar"]

# Run the uberjar when the image is started
CMD ["java", "-jar", "target/uberjar/clj_lein-0.1.0-SNAPSHOT-standalone.jar"]

