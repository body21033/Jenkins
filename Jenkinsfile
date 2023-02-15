pipeline {
    agent any
    environment {
      PROJECT_NAME = "Uran238"
      OWNER_NAME   = "Bohdan2"
      Log ="console"
      Chng= "changes"
      Good_work = """
      *Project/Branch - ${JOB_NAME}*
      \n*Deploy Finished: SUCCESS*
      \nBuild number - ${BUILD_NUMBER}
      \nLog - ${BUILD_URL}${Log}
      \nGit Commit details - ${BUILD_URL}${Chng}
      """
      Bad_work = """
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
        stage('2-Tests') {
            steps {
                echo "Start of Stage Test..."
                echo "Testing......."
                echo "Privet ${PROJECT_NAME}"
                echo "Owner is ${OWNER_NAME}"
                echo "End of Stage Build..."
            }
        }
        stage('3-Notify') {
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
            telegramSend "$env.Good_work"
                }
        failure {
            telegramSend "$env.Bad_work"
                }
        }
}