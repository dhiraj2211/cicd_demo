pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                echo 'testing'
            }
        }
        stage('Deploy') {
            steps {
                sh 'ssh -o StrictHostKeyChecking=no dhiraj@192.168.57.10 "cd cicd_demo;\
                source env/bin/activate;\
                git pull origin main;\
                pip install -r requirements.txt --no-warn-script-location;\
                python manage.py migrate;\
                deactivate;\
                sudo systemctl restart nginx;\
                sudo systemctl restart gunicorn"'
            }
        }
    }
}