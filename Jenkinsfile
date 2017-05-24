#!/usr/bin/env groovy

node {
      stage('checkout') {
      echo "Download do Projeto do GIT"
      git 'https://github.com/Supertchuco/otto-rest.git'

      echo "Buildando"
      sh 'chmod +x gradlew'
      sh './gradlew build -x test'

      archive 'build/libs/*.jar'
    }

    stage('checking Java version') {
    	env.JAVA_HOME="${tool 'JDK 1.8'}"
    	env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
            sh "java -version"
    }

    stage('unit tests') {
	     echo 'TBD'
    }

    stage('integration tests') {
      echo 'integration tests'
    }

    stage('code coverage') {
	     sh "/bin/bash ./otto-rest/gradlew --build-file otto-rest/build.gradle"
    }

    stage('publishing code coverage reports') {
      echo 'Jacoco'
    }


    stage('archiving artifacts') {
        sh "/bin/bash ./otto-rest/gradlew --build-file otto-rest/build.gradle bootRepackage -x test -Pdi"
        archiveArtifacts artifacts: '**/otto-rest/build/libs/*.jar', fingerprint: true
    }

    stage('generating docker image') {
    	sh 'docker build -t ./otto-rest/.'
    }

    stage('pushing docker image to Docker Hub'){
  	   echo 'publish docker hub'
  	}
    }

    stage('notification') {
	echo 'Notification TBD'
    }
}
