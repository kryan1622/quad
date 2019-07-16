pipeline{
agent any
        stages{ 
		stage('---delete---'){
                        steps{
                                sh "kubectl delete -f ./server"
                        }
                }

                stage('---rebuild---'){
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
