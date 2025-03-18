# setups-for-automation-deployment-project
tools: git, GitHub, Jenkins, maven, nexus, SonarQube, tomcat.

This project involves writing a Jenkins pipeline to achieve continuous integration (CI) by getting the source code from GitHub, building the code using Maven, and storing artifacts on Nexus. The pipeline also incorporates a rollback mechanism in case of build failure. Additionally, it scans the source code using SonarQube for bugs and code smells. Once the source code is validated, the web application is deployed on a Tomcat server.
