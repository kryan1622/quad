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
                stage('---delete---'){
                        steps{
                                sh "kubectl apply -f ./client"
                        }
                }
                stage('---rebuild---'){
                        steps{
                                sh "kubectl apply -f ./client"
                        }
                }
                stage('---rebuild---'){
                        steps{
                                sh "kubectl apply -f ./nginx"
                        }
                }
        }
}
