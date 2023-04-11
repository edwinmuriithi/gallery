pipeline{
    agent any
    tools{
        nodejs 'NodeJS19'
    }
    stages{
        stage('Clone repository'){
            steps {
                 git 'https://github.com/edwinmuriithi/gallery.git'
            }
        }
        stage('Install dependencies'){
            steps{
                sh 'npm install' 
            }
        }
    }
}