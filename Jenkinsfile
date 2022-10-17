pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('dockerhub')
    }
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
                sh 'ls *'
            }
        }
        stage('Build Image') {
            steps {
		    sh "docker build -t atiemwenjoseph/pipeline:python ."
		    sh "docker logout"
	    }
	}
        stage('Docker Push') {
            steps {
		    withDockerRegistry(credentialsId: 'Demo-creds-DockerHub', url: '') {
			    sh "docker image push atiemwenjoseph/pipeline:latest"
              }
          }
        }
    post {
		always {
			sh 'docker logout'
		}
	 }
    }

