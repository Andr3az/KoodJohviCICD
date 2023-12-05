pipeline{
    agent any
    tools{
        nodejs 'nodejs18'
    }
    stages {
        stage ('Checkout'){
            steps{
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/danielaburnaz/KoodJohviCICD/'
            }
        }
        stage('npm install'){
            steps{
                script{
                    sh 'npm install'
                }
            }
        }
        stage("build application"){
            steps{
                script{
                        sh "mkdir -p /kj_deployments/aburnaz_${env.BRANCH_NAME}"
                        sh 'npm run build'
                        sh "cp -r dist/kood-johvi-cicd/browser/* /kj_deployments/aburnaz_${env.BRANCH_NAME}"
                        discordSend description: 'Build complete', footer: '', image: '', link: '', result: '', scmWebUrl: '', thumbnail: '', title: '', webhookURL: 'https://discord.com/api/webhooks/1181574091526897705/oEyRPsEtmJXsRrydGbpec3gyJ3QIF_YbSIDfFrv7-fZSfRfbjPyULGPCfQzfWw7zvI7n'
                    
                }
            }
        }
    }
}
