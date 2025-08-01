pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Docker build') {
            steps {
                echo "Docker Image build "
                script {
                    withDockerRegistry(credentialsId: 'docker_key'){
                        sh '''
                        pwd
                        docker build -t nodejs .
                        docker tag nodejs swagatdevops/nodejs:${BUILD_NUMBER}
                        docker push swagatdevops/nodejs:${BUILD_NUMBER}
                        docker run -d -p 8081:3000 --name swagat nodejs 
                        '''  
                    }
                }
            }
        }
    }
}
