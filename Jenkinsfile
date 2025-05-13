pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-hub')
    }
    stages {
        stage("git clone") {
            steps {
                git branch: 'main', url: 'https://github.com/spoorthibk75/java-springboot-app.git'
            }
        }
        stage("package") {
            steps {
                sh 'mvn clean package'
            }
        }
        stage("docker build") {
            steps {
                sh 'docker build -t spoorthibk/springbootapp:latest .'
            }
        }
        stage("docker-login") {
            steps {
                sh 'echo "$DOCKERHUB_CREDENTIALS_PSW" | docker login -u "$DOCKERHUB_CREDENTIALS_USR" --password-stdin'
            }
        }
        stage("docker-push") {
            steps {
                sh 'docker push spoorthibk/springbootapp:latest'
            }
        }
        stage("docker container") {
            steps {
                sh 'docker run -d -p 8095:8085 --name app spoorthibk/springbootapp:latest'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')]) {
                    sh 'kubectl apply -f deployment.yaml'
                    sh 'kubectl apply -f service.yaml'
                }
            }
        }
    }
}
