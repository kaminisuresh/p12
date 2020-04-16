pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout'
            }
        }
        stage('Build') {
            steps {
                echo 'Clean Build'
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                sh 'mvn test'
            }
        }
        stage('JaCoCo') {
            steps {
                echo 'Code Coverage'
                jacoco()
            }
        }
        stage('Sonar') {
            steps {
                echo 'Sonar Scanner'
               	script{
           
        sonarscanner1= tool 'sonars_scanner6'  
        withSonarQubeEnv('sonar6'){
          sh "${sonarscanner1}/bin/sonar-scanner.sh --debug -Dsonar.projectName=$JOB_NAME -Dsonar.projectKey=$JOB_NAME -Dsonar.projectVersion=1.0.0 -Dsonar.sources=src/main -Dsonar.java.binaries=target/classes -Dsonar.tests=src/test -Dsonar.junit.reportsPath=/target/surefire-reports -Dsonar.junit.reportsPath=/target/surefire-reports -Dsonar.jacoco.reportPath=target/jacoco.exec -Dsonar.jacoco.reportPath=target/jacoco.exec -Dsonar.language=java -Dsonar.sourceEncoding=UTF-8 "  
        }
		}
		    
            }
        }
        
        stage('Deploy') {
            steps {
                echo '## TODO DEPLOYMENT ##'
            }
        }
    }
    
    post {
        always {
            echo 'JENKINS PIPELINE'
        }
        success {
            echo 'JENKINS PIPELINE SUCCESSFUL'
        }
        failure {
            echo 'JENKINS PIPELINE FAILED'
        }
        unstable {
            echo 'JENKINS PIPELINE WAS MARKED AS UNSTABLE'
        }
        changed {
            echo 'JENKINS PIPELINE STATUS HAS CHANGED SINCE LAST EXECUTION'
        }
    }
}
