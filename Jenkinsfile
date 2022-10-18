pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
                sh 'ls *'
            }
        }
        stage('Build Image') {
            steps {
		    sh "docker build -t atiemwenjoseph/pipeline:python3 ."
		    sh "docker logout"
	    }
	}
        stage('Docker Push') {
            steps {
		    withDockerRegistry(credentialsId: 'Demo-creds-DockerHub', url: '') {
			    sh "docker image push atiemwenjoseph/pipeline:python3"
              }
          }
		stage('Trigger File Triggered') {
		steps {
			build 'Trigger File'
	    }
	}
        }
    }

}

//     post {
// 		always {
// 			sh 'docker logout'
// 		}
// 	 }
//     }
