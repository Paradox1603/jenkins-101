pipeline {
    agent { 
        node {
            label 'python-agent'
            }
      }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                echo "doing build stuff.."
                cd myapp
                python3 -m venv venv
                . venv/bin/activate

                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                echo "doing test stuff.."
                cd myapp

                . venv/bin/activate
                
                python3 hello.py
                python3 hello.py --name=Kevin
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}