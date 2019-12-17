pipeline {
    agent any
    environment {
        PATH = "${PATH}:${tool name: 'maven3', type: 'maven'}/bin"
    }
    stages {
        stage ('SCM Checkout'){
            steps {
                git credentialsId: 'git-1',
                url: 'https://github.com/pranatgit/jenkins-pranat-javahomes',
                branch: 'master'
            }
        }
        stage ('Maven Build'){
            steps {
               sh "mvn clean package"
            }
        }
        stage ('Deploy dev') {
            steps {
                sshagent(['tomcat-dev']) {
                     // stop tomcat
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@18.224.94.59 /opt/tomcat8/bin/shutdown.sh"
                    // copy war file to remote tomcat
                    sh "scp target/6pmwebapp.war  ec2-user@18.224.94.59:/opt/tomcat8/webapps/"
                    // start tomcat
                     sh "ssh ec2-user@18.224.94.59 /opt/tomcat8/bin/startup.sh"
                }
            }
        }
    }
    post {
        success {
            mail bcc: '',
            body: 'successfully deployed jenkins', 
            cc: '', 
            from: '', 
            replyTo: '', 
            subject: 'successfully deployed', 
            to: 'pranatmund5@gmail.com'
        }
    }
}
