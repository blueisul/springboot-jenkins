pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                echo "Test"
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
            chmod 777 gradlew
            ls -al
            ./gradlew clean print
            java -jar build/libs/demo-0.0.1-SNAPSHOT.jar 
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}