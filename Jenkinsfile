@Library('my-shared-library') _

pipeline{

    agent any 

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }


    stages{

        
        stage('Git Checkout'){
        when { expression { params.action == 'create' } }

            steps{

                gitCheckout(
                      branch: "main",
                      url: "https://github.com/maheswar443/java-proj.git"
                   ) 
                
            }
        }
        stage('Unit Test Maven'){
        when { expression { params.action == 'create' } }
            steps{
 
               script{

                  mvnTest()
               }
                
            }
        }
        stage('Integration Test Maven'){
        when { expression { params.action == 'create' } }

            steps{
 
               script{

                  mvnIntegrationTest()
               }
                
            }
        }
        
    }
}