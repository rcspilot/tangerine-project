pipeline {
    agent any

    stages {
        stage('Build DockerFile') {
            steps {
                echo 'Starting Build'
            }
        }
        stage('Push GCP') {
            steps {
                echo 'Begin Push'
            }
        }
        stage('Apply k8s YAML ') {
            steps {
                parallel(
                    API1_Deployment: {
                        echo "Deploy Api #1"
                        build job: 'Job_1'
                        },
                    API2_Deployment: {
                        echo "Deploy Api #2"
                        build job: 'Job_2'
                        },
                    API3_Deployment: {
                        echo "Deploy Api #3"
                        build job: 'Job_H'
                        }
                )
            }
        }
        stage('Service YAML') {
            steps {
                echo 'Starting Deploy'
            }
        }
    }
}
