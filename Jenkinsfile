pipeline {
 
  agent {
        docker {
            image 'maven:3-alpine'
            args '-v $HOME/.m2:/root/.m2'
        }
    }

  stages {

    stage('Test') {

      steps{
     
        sh 'mvn --version'

        sh 'mvn clean com.smartbear.soapui:soapui-maven-plugin:test'
        
      }

    }

    stage('Results') {

      steps{
  
        junit '**/target/*.xml'

        archive 'target/*'
       sh 'echo "bye-world"'
		

      }

    }

  }

}
