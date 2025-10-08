pipeline{
    agent any
    stages{
        stage("Build Docker Image"){
            steps{
                echo "Build Docker image"
                bat "docker build -t kubdemoapp:v1 ."
            }
        }
        stage("Docker Login"){
            steps{
                bat "docker login -u tejashwini1108 -p Tejashwini@1108"
            }
        }
        stage("push Docker image to docker hub"){
            steps{
                echo "push Docker image to docker hub"
                bat "docker tag kubdemoapp:v1 tejashwini1108/week8kubernetes:t1"
                bat "docker push tejashwini1108/week8kubernetes"
            }
        }
        stage("Deploy to kubernetes"){
            steps{
                echo "Deploy to kubernetes"
                bat "kubectl apply -f deployment.yaml --validate=false"
                bat "kubectl apply -f service.yaml"
            }
        }
    }
    post{
        success{
            echo "Pipeline executed successfully"
        }
        failure{
            echo "pipeline failed.Please check the logs"
        }
    }
}
