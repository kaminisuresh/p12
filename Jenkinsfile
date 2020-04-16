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
        withSonarQubeEnv('sonars_scanner6'){
          sh "${sonarscanner1}/bin/sonar-scanner.sh --debug -Dsonar.projectName=$JOB_NAME -Dsonar.projectKey=$JOB_NAME -Dsonar.projectVersion=1.0.0 -Dsonar.modules=gameoflife-core,gameoflife-web -Dgameoflife-core.sonar.java.binaries=target/classes -Dgameoflife-web.sonar.java.binaries=target/classes -Dgameoflife-core.sonar.sources=src/main -Dgameoflife-web.sonar.sources=src/main -Dgameoflife-core.sonar.tests=src/test -Dgameoflife-web.sonar.tests=src/test -Dgameoflife-core.sonar.junit.reportsPath=/target/surefire-reports -Dgameoflife-web.sonar.junit.reportsPath=/target/surefire-reports -Dgameoflife-core.sonar.jacoco.reportPath=target/jacoco.exec -Dgameoflife-web.sonar.jacoco.reportPath=target/jacoco.exec -Dsonar.language=java -Dsonar.sourceEncoding=UTF-8 "  
        }
		}
		    
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging'
                sh 'mvn package -DskipTests'
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
