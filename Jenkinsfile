pipeline {
  agent {
    //En lugar de any especificamos el nodo que queremos (cuando tenemos mas de un nodo)
    node {
      label 'principal'
    }
  }
  
  options {
    //para ficheros log, para descartar
    buildDiscarder logRotator(
      daysToKeepStr: '15',
      numToKeepStr: '10'
      )
  }
  
  stages {
    
    stage('Cleanup Workspace') {
      
      steps {
        cleanWs()
        echo "Eliminado Worksapce para Proyecto"
      }
      
    }
    
    stage('Code Checkout') {
      
      steps {
        checkout (
          $class: 'GitSCM',
          branches: [[name: '*/main']],
          userRemoteConfigs: [[url:'https://github.com/spring-projects/spring-petclinic.git']]
          )
      }
      
    }
    
    stage('Unit Testing') {
      
      steps {
         echo "Running Unit Tests"
      }
      
    }
    
    stage('Code Analysis') {
      
      steps {
         echo "Running Code Analysis"
      }
      
    }
    
    stage('Build Deploy Code') {
      
      when {
        branch 'developer'
      }
      steps {
         echo "Building Artifact"
        
         echo "Deploying Code"
      }
      
    }
    
  }
  
  
}
