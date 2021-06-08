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
        stage ('Invoke_JobH') {
            steps {
                build job: 'Job_H', parameters: [
                string(name: 'param1', value: "value1")
                ]
            }
        }
        stage('Apply k8s YAML ') {
            steps {
                parallel(
                    API1_Deployment: {
                        echo "Deploy Api #1"
                        sleep 5
                        },
                    API2_Deployment: {
                        echo "Deploy Api #2"
                        sleep 5
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
