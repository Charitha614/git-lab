pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Application'

                sh '''
                mkdir -p build
                cp *.txt build/
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests'

                sh '''
                test -f build/app.txt
                test -f build/feature.txt
                test -f build/changelog.txt
                test -f build/release-plan.txt
                '''
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging Application'

                sh '''
                tar -cvf git-lab-package.tar build/
                '''
            }
        }

        stage('Deploy') {
            steps {

                echo 'Deploying Application'

                sh '''
                cp git-lab-package.tar /opt/deployments/git-lab/
                '''
            }
        }
    }

    post {

        success {
            echo 'Pipeline Successful'
        }

        failure {
            echo 'Pipeline Failed'
        }

    }
}
