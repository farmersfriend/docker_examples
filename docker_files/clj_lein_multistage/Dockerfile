FROM clojure:openjdk-11-lein-2.9.3-buster as foundation

WORKDIR /app




FROM foundation as dev

CMD ["lein", "run"]




FROM foundation

# Install deps
COPY project.clj ./
RUN ["lein", "deps"]

# Generate the uberjar
COPY . ./
RUN ["lein", "uberjar"]

# Run the uberjar when the container starts
CMD ["java", "-jar", "target/uberjar/clj_lein-0.1.0-SNAPSHOT-standalone.jar"]
