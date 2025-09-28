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
        // stage("Owasp Dependency Check"){
        //     steps{
        //         sh 'mvn org.owasp:dependency-check-maven:9.0.10:check'
        //     }
        // }
        stage('SAST') {
            steps { 
                echo "Running Static application security testing using SonarQube Scanner ..."
                withSonarQubeEnv('sonar-server') {
                    sh 'mvn sonar:sonar -Dsonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml -Dsonar.projectName=spb'
                }
            }
        }
    }
}