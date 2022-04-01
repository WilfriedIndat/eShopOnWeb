pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Unit Test') {
      parallel {
        stage('Unit Test') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('Integration Tests') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Functional Tests') {
          steps {
            sh 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}