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
}

