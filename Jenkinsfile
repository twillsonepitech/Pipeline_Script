pipeline {
    agent any
    stages {
        stage('Git-Checkout') {
            steps {
                echo "Checking out from Git Repo";
                git 'https://github.com/twillsonepitech/Pipeline_Script.git'
            }
        }
        stage('Debug') {
            steps {
                echo "Contents of workspace directory:"
                sh 'ls -l'
            }
        }

        stage('Build') {
            steps {
                echo "Building the checked-out project!";
                sh 'sh Build.sh'
            }
        }

        stage('Unit-Test') {
            steps {
                echo "Running JUnit Tests";
                sh 'sh Unit.sh'
            }
        }

        stage('Quality-Gate') {
            steps {
                echo "Verifying Quality Gates";
                sh 'sh Quality.sh';
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying to Stage environment for more tests!";
                sh 'sh Deploy.sh';
            }
        }
    }
    
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
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
