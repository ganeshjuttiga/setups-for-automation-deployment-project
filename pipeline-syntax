pipeline{
    agent any
    stages{
        stage('Code'){
            steps{
                git 'https://github.com/AvinashSaladi/one.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Test'){
           steps{
                script{
                    withSonarQubeEnv('mysonar'){
                      def mavenHome = tool name: "maven", type: "maven"
                      def mavenCMD = "${mavenHome}/bin/mvn"
                      sh "${mavenCMD} sonar:sonar"
                    }
                }
            }
        }
        stage('Artifact'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'target/myweb-8.6.7.war', type: 'war']], credentialsId: 'nexus', groupId: 'in.javahome', nexusUrl: '54.226.180.96:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'myrepo', version: '8.6.7'
            }
        }
        stage('Deployment'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'd9b6f640-e660-4eb2-b53b-263aad417f5f', path: '', url: 'http://54.198.64.104:8080')], contextPath: 'luffy', war: 'target/*.war'
            }
        }
    }
}
