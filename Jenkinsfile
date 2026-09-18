pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Pulling website code...'
             
        }git branch: 'main', credentialsId: '9469f846-43ca-4b97-805e-7a19023dace6', url: 'https://github.com/deepubhakuni5/static-website1.git'
        }

        stage('Build Docker Image') {
            steps {
                powershell """
                    docker build -t static-website:latest .
                """
            }
        }

        stage('Run Container') {
            steps {
                powershell """
                    docker stop static-web 2>\$null
                    docker rm static-web 2>\$null
                    docker run -d --name static-web -p 5553:80 static-website:latest
                """
            }
        }
    }

    post {
        success {
            echo "Website running at: http://localhost:5353"
        }
    }
}
