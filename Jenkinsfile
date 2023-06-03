@Library('my-shared-library') _

pipeline{

    agent any 

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }


    stages{

        when { expression { param.action == 'create' } }
        
        stage('Git Checkout'){

            steps{

                gitCheckout(
                      branch: "main",
                      url: "https://github.com/maheswar443/java-proj.git"
                   ) 
                
            }
        }
        stage('Unit Test Maven'){
        when { expression { param.action == 'create' } }
            steps{
 
               script{

                  mvnTest()
               }
                
            }
        }
        stage('Integration Test Maven'){
        when { expression { param.action == 'create' } }

            steps{
 
               script{

                  mvnIntegrationTest()
               }
                
            }
        }
        stage('Statis code analysis: Sonarqube'){
        when { expression { param.action == 'create' } }

            steps{
 
               script{

                  statiCodeAnalysis()
               }
                
            }
        }
    }
}