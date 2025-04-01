#base image
FROM alpine/java:22-jdk

#creating working directory
WORKDIR /app

#copy source code into working directory
COPY src/Main.java /app/Main.java 

#compile java file 
RUN javac Main.java

#run java file 
CMD ["java", "Main"]


##source code -->
##https://github.com/LondheShubham153/simple-java-docker.git