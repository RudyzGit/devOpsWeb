pipeline {
    agents any
    tools{
        maven 'maven3'
    }
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deploy to a tomcat server'){
            steps {
                deploy adapters: [tomcat9(credentialsId: 'a2cd7e7c-1d54-430b-bd91-b2f740bf932d', path: '', url: 'http://localhost:8080/')], contextPath: null, war: '**/*.war'
                    }
                }
            }
        }
