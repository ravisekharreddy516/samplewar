node{
    
    def mavenHome = tool name: "maven3.8.6"
    stage('Checkout Code'){
        git credentialsId: 'dbd86b09-be77-409b-ab77-95005a625054', url: 'https://github.com/ravisekharreddy516/samplewar.git'
    }
    stage('Build'){
        sh "${mavenHome}/bin/mvn clean package"
    }
    stage('DeployApplicationIntoTomcat')
    {
     sshagent(['slave-credentials']) {
    sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Pipelinejob/target/sparkjava-hello-world-1.0.war ubuntu@3.109.139.246:/opt/tomcat9/webapps/"
}   
    }
    stage('Send Email Notification')
    {
        emailext body: 'Build is successful', subject: 'Build Is Over...!!', to: 'ravi@gmail.com'
    }
}
