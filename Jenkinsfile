Piepline{
    agent any

    stages{

        stage('Conditional Stage'){

            when{
                expression {
                    return env.BRANCH_NAME == 'main' || env.BRANCH_NAME.startsWith('feature')
                }
            }

            stages{
                stage("Checkout SCM"){
                
                    checkout scm
                }
                stage("Set up Dotnet"){
                    steps{
                        bat 'dotnet --version'
                        bat 'winget install Microsoft.DotNet.SDK.6 --source winget'
                    }
                }

                stage("Build Solution"){
                    steps{
                        bat 'dotnet build'
                    }
                }

                stage("Run Tests"){
                    steps{
                        bat 'dotnet test'
                    }
                }
            }

        }

    }

}

// minor change