pipeline{
    agent{
        label "Jenkins-agent"
    }
    tools {
        jdk 'Java17'
        maven 'Maven3'
    }
    stages{
        stage("Cleanup Workspace"){
            steps {
                cleanWs()
            }

        }

    stage("Checkout from SCM"){
       steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/rohit1456/complete-prodcution-e2e-pipeline'
            }

       }

    stage("Build application"){
       steps {
                sh "mvn clean package"
            }

       }

    stage("Test application"){
       steps {
                sh "mvn test"
            }

       }

    stage("sonarqube analysis"){
       steps {
            script {
                withSonarQubeEnv(credentialsID: 'Jenkins-sonarqube-token') {
                    sh "mvn sonar:sonar"
            }

       }

    }
}
