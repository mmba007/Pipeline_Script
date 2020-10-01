pipeline {
    agent any
    stages {

      	stage('Git-Checkout') {

              steps {
                      echo '*********** Checking out from git repo' ;
                      git 'https://github.com/mmba007/Pipeline_Script.git'
                      }
              }


        stage('Build') {
            steps {
                echo '*********** Building the checkout project' ;
                sh 'Build.sh'
                }
        }

        stage('Unit-Test') {
            steps {
                echo '*********** Running JUnit Tests' ;
                sh 'Unit.sh'
                }
        }

        stage('Quality-Gate') {
            steps {
                echo '*********** Verifying quality gates' ;
                sh 'Quality.sh'
                }
        }

        stage('Deploy') {
            steps {
                echo '*********** Deploying to stage environment for more tests' ;
                sh 'Deploy.sh'
                }
        }

    }
    post{
        always{
            echo '########## This will always run'

        }

        success{
            echo '########## This will run only if successful'

        }

        failure{
            echo '########## This will run only if failed'

        }

        unstable{
            echo '########## This will run only if the run was marked as unstable'

        }

        changed{
            echo '########## This will run only if the state of the pipeline has changed'
            echo '########## For example, if the pipeline was previously failing but is now successful'
        }


    }

}
