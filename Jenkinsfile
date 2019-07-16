pipeline{
	agent any
        stages{
		stage('---get pods---'){
                        steps{
                               sh "kubectl get pods"
                        }
                }
		
                stage('---docker---'){
                        steps{
                                 sh "sudo docker ps"
                                 sh "sudo docker-compose build client"
                                 sh "sudo docker-compose build server"
                                 sh "sudo docker-compose build nginx"
                                 sh "sudo docker push kryan1622/kube/my/server:latest"
                                 sh "sudo docker push kryan1622/kube/my/client:latest"
                        }
                }

		stage('---patches---'){
                        steps{
                                 sh "kubectl patch deployment server -p "{\"spec\":{\"template\":{\"metadata\":{\"labels\":{\"date\":\"`date +'%s'`\"}}}}}""
                                 sh "kubectl patch deployment client -p "{\"spec\":{\"template\":{\"metadata\":{\"labels\":{\"date\":\"`date +'%s'`\"}}}}}""
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
	}
}

