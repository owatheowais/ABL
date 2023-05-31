# Use a base image with the desired Linux distribution and version
FROM ubuntu:22.04

# Set environment variables for MySQL installation
ENV MYSQL_ROOT_PASSWORD=abc12345
ENV MYSQL_DATABASE=whatsapp
ENV MYSQL_USER=admin
ENV MYSQL_PASSWORD=abc12345

# Update the package manager and install MySQL Server 8.0
RUN apt-get update && \
    apt-get install -y mysql-server-8.0

# Copy custom configuration (optional)
# If you have a custom MySQL configuration file, you can copy it to the container.
# Uncomment the following lines and place your configuration file in the same directory as this Dockerfile.
# COPY my.cnf /etc/mysql/my.cnf

# Expose MySQL port (default is 3306)
EXPOSE 3306

# Start MySQL service on container startup
CMD ["mysqld"]

# Note: The CMD instruction starts the MySQL service, but it doesn't provide a detached mode.
# To run the container in detached mode, you can modify the CMD instruction to:
# CMD ["mysqld", "--daemonize"]
