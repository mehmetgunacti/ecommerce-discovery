pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "ecommerce-discovery"
    }
    stages {
        stage('Clone Repositories') {
            steps {
                sh 'rm -rf ecommerce-parent && git clone https://github.com/mehmetgunacti/ecommerce-parent.git'
                sh 'rm -rf ecommerce-discovery && git clone https://github.com/mehmetgunacti/ecommerce-discovery.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'cd ecommerce-discovery && mvn clean package'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8761:8761 --name $DOCKER_IMAGE $DOCKER_IMAGE:latest'
            }
        }
    }
}