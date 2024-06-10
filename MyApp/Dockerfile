FROM tomcat:9.0

# Add the WAR file to the webapps directory
ADD ./target/*.war /usr/local/tomcat/webapps/

# Expose port 9000
EXPOSE 9000

# Set the working directory to Tomcat's bin directory
WORKDIR /usr/local/tomcat/bin

# Command to start Tomcat
CMD ["catalina.sh", "run"]
