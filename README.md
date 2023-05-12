# Continuous Integration and Deployment with Jenkins and GitHub
In this assessment task, you will be required to create a Jenkins pipeline that integrates with GitHub.

## Define a pipeline with 7 stages. The stages should include:
- [x] Stage 1: Build - Build the code using a build automation tool to compile and package your code. You need to specify at least one build automation tool e.g., Maven.  
- [x] Stage 2: Unit and Integration Tests - run unit tests to ensure the code functions as expected and run integration tests to ensure the different components of the application work together as expected. You need to specify test automation tools for this stage.
- [x] Stage 3: Code Analysis - integrate a code analysis tool to analyse the code and ensure it meets industry standards. Research and select a tool to analyse your code using Jenkins.  
- [x] Stage 4: Security Scan - perform a security scan on the code using a tool to identify any vulnerabilities. Research and select a tool to scan your code.
- [x] Stage 5: Deploy to Staging - deploy the application to a staging server (e.g., AWS EC2 instance).  
- [x] Stage 6: Integration Tests on Staging - run integration tests on the staging environment to ensure the application functions as expected in a production-like environment.
- [x] Stage 7: Deploy to Production - deploy the application to a production server (e.g., AWS EC2 instance).
