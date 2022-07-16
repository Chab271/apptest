pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent any
    stages {
        
        stage('build and push') {
            steps { 
                    sh"sudo docker build -t aymenchab/apptest:1.0 ."                  
                    withDockerRegistry([url: "", credentialsId: "4a93d596-7aea-4b4a-8cd6-b943dc482a36"]) {
                        sh"docker push aymenchab/apptest:1.0"
                }
            }
            }
       stage ('make pod') {
           steps {  
                   sh"sudo kubectl apply -f deployment.yml --namespace=test"
           }
           }
           stage ('make service') {
           steps { 
                   sh"sudo kubectl apply -f service.yml --namespace=test"
           }
           }
         }
}
