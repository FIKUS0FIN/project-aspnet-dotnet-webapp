pipeline {
  agent {
    node {
      customWorkspace "ws\\${JOB_NAME.replace("%2F", "_")}"
      label 'windows'
    }

  }
  stages {
    stage('msbuild-info') {
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