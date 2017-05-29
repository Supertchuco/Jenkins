#!/usr/bin/env groovy

node {
    stage('BUILD') {
      echo "Download do Projeto do GIT"
      git 'https://github.com/Supertchuco/otto-rest.git'

      echo "Buildando"
      sh 'chmod +x gradlew'
      sh 'sudo ./gradlew clean build buildDocker'

    }

    stage('generating docker image') {
    	echo "sh sudo docker build ."
    }

    stage('pushing docker image to DTR'){
      echo "publish docker hub"
	}


    stage('notification') {
	     echo 'Notification TBD'
    }
}
