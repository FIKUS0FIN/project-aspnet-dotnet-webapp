pipeline {
  agent {
    node {
      customWorkspace "ws\\${JOB_NAME.replace("%2F", "_")}"
      label 'windows'
    }

  }
  stages {
    stage('Build app') {
      parallel {
        stage('msbuild-info') {
          steps {
            bat 'nuget restore'
            bat "\"${tool 'MSBuild-deff'}\" SampleWebApplication.sln"
          }
        }
        stage('tree') {
          steps {
            bat 'tree'
          }
        }
      }
    }
  }
}