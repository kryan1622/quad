pipeline{
	agent any
        stages{
		stage('---clean---'){
                        steps{
                               sh "kubectl delete -f ./nginx/config-map.yaml"
                               sh "kubectl delete -f ./nginx/deployments.yaml"
                        }
                }
		stage('---get pods---'){
                        steps{
                               sh "kubectl get pods"
                        }
                }
		stage('---mongo---'){
                        steps{
                               sh "kubectl apply -f ./mongo/pod.yaml"
                               sh "kubectl apply -f ./mongo/service.yaml"
                        }
                }
		stage('---client---'){
			steps{
				sh "kubectl apply -f ./client/deployment.yaml"
				sh "kubectl apply -f ./client/service.yaml"
			}
		}
		stage('---server---'){
			steps{
				sh "kubectl apply -f ./server"
			}
		}
		stage('---nginx---'){
			steps{
				sh "kubectl apply -f ./nginx"
			}
		}
                stage('---docker---'){
                        steps{
                                 sh "sudo docker ps"
                                 sh "sudo docker-compose build client"
                        }
                }		
	}
}

