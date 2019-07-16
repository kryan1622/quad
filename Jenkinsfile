pipeline{
agent any
        stages{ 
		stage('---delete1---'){
                        steps{
                                sh "kubectl delete -f ./server"
                        }
                }

                stage('---rebuild1---'){
                        steps{
                                sh "kubectl apply -f ./server"
                        }
                }
                stage('---delete2---'){
                        steps{
                                sh "kubectl apply -f ./client"
                        }
                }
                stage('---rebuild2---'){
                        steps{
                                sh "kubectl apply -f ./client"
                        }
                }
                stage('---rebuild3---'){
                        steps{
                                sh "kubectl apply -f ./nginx"
                        }
                }
        }
}
