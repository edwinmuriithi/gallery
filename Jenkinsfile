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
        stage('Tests'){
            post{
                failure{
                    mail bcc: '', body: 'Build failed. Check on repository.', cc: '', from: '', replyTo: '', subject: 'Build Failure', to: 'kabuimuriithi@gmail.com'
                }
            }
            steps{
                sh 'npm test'
            }
        }
        stage('Deploy on Render'){
            steps{
                renderDeploy(
                    credentialsId: 'RENDER_CREDENTIALS',
                    serviceId: 'srv-cgqpti3k9u5es1410ss0',

                )
                
                
            }
        }
        
    }
}

// withCredentials([usernameColonPassword(credentialsId: 'render', variable: 'RENDER_CREDENTIALS')]) {
//                 sh 'git push https://api.render.com/deploy/srv-cgqpti3k9u5es1410ss0?key=_s20vqRg2mo'