pipeline{
	agent any
	stages{
	    stage('Build Docker IAmge'){
	        steps{
                echo "Build Docker Image"
                bat "docker build -t tejashwini1108/week9:t2 ."
	        }
	    }
	    stage('Docker Login'){
	        steps{
                bat "docker login -u tejashwini1108 -p Tejashwini@1108"
	        }
	    }
        stage('push Docker Image to Docker Hub'){
            steps{
                echo "push Docker image to docker hub"
                bat "docker push tejashwini1108/week9:t2"
            }
        }
        stage('Deploy to Kuberentes'){
            steps{
                echo "Deplot to kubernetes"
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml'
            }
        }
	}
	post{
	    success{
	        echo 'Pipeline completed successfully!'
	    }
	    failure{
	        echo 'Pipeline failed.Please check the logs'
	    }
	}
}
