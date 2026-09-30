pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package'
                sh 'echo Hello world iam luffy
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

                        git fetch origin main:refs/remotes/origin/main feature:refs/remotes/origin/feature

                        git checkout -B main origin/main

                        git merge origin/feature --no-edit

                        git push https://${GIT_USER}:${GIT_TOKEN}@github.com/Shanmukh092/my-java-app.git main
                    '''
                }
            }
        }

    }
}
