pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'La construction va dÃƒÂ©marrer'
        bat 'mvn -Dskiptests clean package'
        echo 'Construction terminÃ©e'
      }
    }

    stage('Test') {
      steps {
        echo 'Démarrage des tests unitaires'
        bat 'mvn -Dtest="com.example.testingweb.smoke.**" test'
        echo 'Fin des tests unitaires'
      }
    }

  }
}