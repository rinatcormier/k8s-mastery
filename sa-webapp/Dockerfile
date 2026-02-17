FROM eclipse-temurin:25-jdk-alpine

# Documentation: EXPOSE acts as a hint to developers and operators about which ports are expected to be available
# for services running inside the container.
# ---
# No Automatic Publishing: By itself, EXPOSE does not make the ports accessible from the host or external network.
# For security reasons, Docker requires explicit publishing.
# ---
# Interaction with docker run -P: When you run a container with the docker run -P (uppercase P, short for --publish-all)
# command, Docker automatically maps all ports specified with EXPOSE in the Dockerfile to random, high-order, available
# ports on the host machine.
EXPOSE 8080

# Environment Variable that defines the endpoint of sentiment-analysis python api.
ENV SA_LOGIC_API_URL http://localhost:5000

# COPY is "Same as 'ADD', but without the tar and remote URL handling."
# In other words, ADD extracts archives automatically while COPY just copies.
COPY target/sentiment-analysis-web-0.0.1.jar sentiment-analysis-web-0.0.1.jar

# Excellent explanation of differences between ENTRYPOINT and CMD instructions:
# https://stackoverflow.com/a/34245657/2892373
# In a short:
# "The ENTRYPOINT specifies a command that will always be executed when the container starts."
# "The CMD specifies arguments that will be fed to the ENTRYPOINT."
ENTRYPOINT ["java", "-jar", "sentiment-analysis-web-0.0.1.jar", "--sa.logic.api.url=${SA_LOGIC_API_URL}"]