pipeline {

  agent any

  tools {

    maven 'mvn'

    jdk 'JDK 8'

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

        junit '**/target/soapui/TEST-*.xml'

        archive 'target/*'

      }

    }

  }

}
