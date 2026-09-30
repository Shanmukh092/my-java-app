pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
		sh 'echo Hello iam luffy'
            }
        }
	stage('Merge to Main') {
		steps {
			sh '''
				git checkout main
				git merge feature
				git push origin main
			'''
		}
	}
    }
stage('Merge') {
    steps {
        withCredentials([
            usernamePassword(
                credentialsId: 'github-pat',
                usernameVariable: 'GIT_USER',
                passwordVariable: 'GIT_TOKEN'
            )
        ]) {
            sh '''
                git config user.email "shanmukh@local"
                git config user.name "Shanmukh"

                git fetch origin

                git checkout -B main origin/main

                git merge origin/feature --no-edit

                git push https://${GIT_USER}:${GIT_TOKEN}@github.com/Shanmukh092/python-project-1.git main
            '''
        }
    }
}
}

