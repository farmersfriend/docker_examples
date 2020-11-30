FROM clojure:openjdk-11-lein-2.9.3-buster

COPY . /app
WORKDIR /app

# Generate the uberjar
RUN ["lein", "uberjar"]

# Run the uberjar
CMD ["java", "-jar", "target/uberjar/clj_lein-0.1.0-SNAPSHOT-standalone.jar"]
