pipeline {
    agent any
    environment {
      PROJECT_NAME = "Uran238"
      OWNER_NAME   = "Bohdan"
      Log ="console"
      Chng= "changes"
      Message_OK = """
      *Project/Branch - ${JOB_NAME}*
      \n*Deploy Finished: SUCCESS*
      \nBuild number - ${BUILD_NUMBER}
      \nLog - ${BUILD_URL}${Log}
      \nGit Commit details - ${BUILD_URL}${Chng}
      """
      Message_NOT_OK = """
      *Project/Branch - ${JOB_NAME}*
      \n*Deploy Finished: FAILURE*
      \nBuild number - ${BUILD_NUMBER}
      \nLog - ${BUILD_URL}${Log}
      \nGit Commit details - ${BUILD_URL}${Chng}
      """
    }

    stages {
        stage('1-Build') {
            steps {
                echo "Start of Stage Build..."
                echo "Building......."
                echo "End of Stage Build..."
            }
        }
        stage('2-Test') {
            steps {
                echo "Start of Stage Test..."
                echo "Testing......."
                echo "Privet ${PROJECT_NAME}"
                echo "Owner is ${OWNER_NAME}"
                echo "End of Stage Build..."
            }
        }
        stage('3-Deploy') {
             when {
                anyOf {
                    branch "main"
                }
            }
            steps {
                echo "Start of Stage Deploy..."
                echo "Deploying......."
                sh "ls -la"
                sh '''
                   echo "Line1"
                   echo "Line2"
                '''
                echo "End of Stage Build..."
            }
        }
        
    }
    post {
        success {
            telegramSend "$env.Message_OK"
                }
        failure {
            telegramSend "$env.Message_NOT_OK"
                }
        }
}