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
            sh 'chmod 777 gradlew'
            sh 'ls -al'
            sh './gradlew clean print'
            sh './gradlew build'
            sh 'BUILD_ID=dontKillMe nohup java -jar build/libs/demo-0.0.1-SNAPSHOT.jar &'
            sh 'curl localhost:8090'
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