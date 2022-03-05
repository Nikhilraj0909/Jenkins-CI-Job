pipeline{
    agent any
    tools{
maven 'Maven-3.8.4'
}
    stages{
        stage('GIT CODE'){
            steps{
                git credentialsId: '29d59c8c-f0ed-4a03-a920-fdbfd314c5b6', url: 'https://github.com/Nikhilraj0909/Jenkins-CI-Job.git'
            }
        }
        stage('BUILD'){
            steps{
                sh "mvn clean package"
            }
        }
        /*
        stage('SonarQube Report'){
            steps{
                sh "mvn clean sonar:sonar"
            }
    }
    stage('Upload Artifactsinto Nexus'){
        steps{
            sh "mvn clean deploy"
        }
    }
    */
    stage('UploadAPP into Tomcat'){
        steps{
            sshagent(['23e59228-d05d-4f19-a234-07dc5d6f7b0f']) {
                  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.127.97.123:/opt/apache-tomcat-9.0.59/webapps/"  
            
        }
}
}
}
}
