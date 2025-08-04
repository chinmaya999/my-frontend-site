pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/chinmaya999/my-frontend-site.git'
            }
        }

        stage('Deploy to Nginx') {
            steps {
                sh '''
                echo "🧹 Cleaning old files..."
                sudo rm -rf /var/www/html/*

                echo "📁 Copying new frontend files..."
                sudo cp -r * /var/www/html/

                echo "🛠️ Setting up /home route..."
                sudo mkdir -p /var/www/html/home
                sudo cp home.html /var/www/html/home/index.html

                echo "📄 Listing deployed files:"
                sudo ls -l /var/www/html/
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployed! Visit: http://192.168.70.55/ and /home'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}

