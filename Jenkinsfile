pipeline {
  agent {
    kubernetes {
      label 'maven-pod-template'
      defaultContainer 'maven-container'
      yamlFile 'KubernetesPod.yaml'
    }
  }
   stages {
    stage('JDK 11 Build & Test') {
      steps {
        container('maven-container-jdk-11') {
          sh 'mvn --version'
          sh 'mvn -B clean package'
        }
      }
      post {
        always {
          junit '**/*.xml'
        }
      }
    }   
}
