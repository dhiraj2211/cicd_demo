pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'pip3 install -r requirments.txt'
            }
        }
        stage('Test') { 
            steps {
                echo 'python3 manage.py test'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'ssh dhiraj@192.168.57.7 "cd cicd_demo;\
                source venv/bin/activate;\
                git pull origin main;\
                pip3 install -r requirments.txt --no-warn-script-location;\
                python3 manage.py migrate;\
                deactivate;\
                sudo systemctl restart nginx;\
                sudo systemctl restart gunicorn;\"'
            }
        }
    }
}