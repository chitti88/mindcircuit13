pipeline {
    agent any

    stages {
        stage('Clone scm') {
            steps {
                echo 'Cloning mc-pipeline project'
				git branch: 'main', url: 'https://github.com/chitti88/mindcircuit13.git'
            }
        }
		stage('Built Artifact') {
            steps {
                echo 'Building artifact with maven tool'
				sh 'mvn clean install'
            }
        }
		stage('Deploying TOMCAT ') {
            steps {
                echo 'Deploying into tocat'
				deploy adapters: [tomcat9(credentialsId: 'tomcat-b13', path: '', url: 'http://54.87.52.91:8091/')], contextPath: 'facebook app', war: '**/*.war'
            }
        }
    }
}
