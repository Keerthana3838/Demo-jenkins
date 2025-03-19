pipeline {
    agent any  // This tells Jenkins to run on any available machine

       stages {
        stage('Checkout Code') {
            steps {
                // This step checks out your code from GitHub
                git  credentialsId : 'PATDemo' ,url : 'https://github.com/Keerthana3838/Demo-jenkins.git', branch:'master' // Replace with your GitHub URL
            }
        }

        stage('install dependencies')
        {
            steps{
                bat '''
                    python -m venv venv
                    call venv\\Scripts\\activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Run Python Script') {
            steps {
                // This step runs the add.py Python script
                bat '''
                call venv\\Scripts\\activate
                pytest test.py
                ''']
            
            }
        }

    stage('Deploy'){

        steps{

            echo 'deploying application'

            bat '''

             call venv\\Scripts\\activate
             python add.py
            '''
        }

    }

    }
    post{
        success{
            echo ' pipeline succeeded'
        }
        failure{
            echo ' pipeline failed!'
        }
    }

}
