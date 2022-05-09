pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'La construction va dÃ©marrer'
        bat 'mvn -Dskiptests clean package'
        echo 'Construction terminée'
      }
    }

    stage('Unit') {
      steps {
        echo 'D�marrage des tests unitaires'
        bat 'mvn -Dtest="com.example.testingweb.smoke.**"'
        echo 'Fin des tests unitaires'
      }
    }

  }
}