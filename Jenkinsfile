pipeline{
    agent{
        label 'agent'
    }
    tools{
        maven 'maven-3.9.11'
    }

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-1.8.0-openjdk-amd64'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages{
        stage("Build & Test"){
            steps{
                sh 'java -version'
                sh 'mvn -version'
            }
        }
    }
}