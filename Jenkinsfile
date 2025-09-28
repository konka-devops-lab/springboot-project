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
                sh 'mvn clean package'
            }
        }
        stage("Code Coverage"){
            steps{
                sh 'mvn jacoco:report'
            }
        }
    }
}