pipeline {
	agent any
	tools {
	    maven "MAVEN3"
	    jdk "OracleJDK11"
	}

	stages {
	    stage('Fetch code') {
            steps {
               git branch: 'main', url: 'https://github.com/kavitha1s/vprofile-project.git'
            }

	    }

	    stage('Build'){
	        steps{
	           sh 'mvn install -DskipTests'
	        }

	        post {
	           success {
	              echo 'Now Archiving it...'
	              archiveArtifacts artifacts: '**/target/*.war'
	           }
	        }
	    }

	    stage('UNIT TEST') {
            steps{
                sh 'mvn test'
            }
        }
	}
}
