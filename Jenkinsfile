pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'La construction va dÃƒÆ’Ã‚Â©marrer'
        bat 'mvn -Dskiptests clean package'
        echo 'Construction terminÃƒÂ©e'
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'DÃ©marrage des tests unitaires'
            bat 'mvn -Dtest="com.example.testingweb.smoke.**" test'
            echo 'Fin des tests unitaires'
          }
        }

        stage('Integration') {
          steps {
            echo 'Début de l\'intégration'
            bat 'mvn -Dtest="com.example.testingweb.integration.**" test'
            echo 'Fin des tests d\'intégration'
          }
        }

        stage('Functional') {
          steps {
            echo 'D�but des tests fonctionnels'
            bat 'mvn -Dtest="com.example.testingweb.functional.**" test'
            echo 'Fin des tests fonctionnels'
          }
        }

      }
    }

  }
}