# Jenkins Shared Library for CI/CD Pipelines

This repository provides a Jenkins shared library that includes reusable Groovy functions for building and deploying Java Maven applications in a Docker environment. These functions can be used in Jenkins pipelines to automate the build and deployment process.

## Repository Structure

- **/vars/**: This folder contains globally accessible Groovy functions that can be used in Jenkins pipelines.
- **/src/com/example/docker.groovy**: This script contains the core logic for building the Docker image, logging into Docker Hub, and pushing the image to a repository.

## Functions Overview

The shared functions are designed to simplify common CI/CD tasks such as:
- **Building the Application JAR**: Compiling the Java application using Maven.
- **Building the Docker Image**: Creating a Docker image from the application.
- **Docker Login**: Authenticating to Docker Hub using credentials stored in Jenkins.
- **Pushing the Docker Image**: Pushing the built Docker image to Docker Hub.

These functions are defined in the `/vars` directory, which Jenkins automatically picks up when using this repository as a shared library. The logic for Docker operations is implemented in the `/src/com/example/docker.groovy` script.

## Usage

1. **Importing the Shared Library**:
   In your Jenkins pipeline, import this shared library using the `library` block as follows:

   ```groovy
   library identifier: 'jenkins-shared-library@master', retriever: modernSCM([
       $class: 'GitSCMSource',
       remote: 'git@github.com:Dakuchi/jenkins-shared-library.git',
       credentialsId: 'Jenkins-shared-lib'
   ])
