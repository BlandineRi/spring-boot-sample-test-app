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
      parallel {
        stage('Test') {
          steps {
            echo 'Démarrage des tests unitaires'
            bat 'mvn -Dtest="com.example.testingweb.smoke.**" test'
            echo 'Fin des tests unitaires'
          }
        }

        stage('Integration') {
          steps {
            echo 'D�but de l\'int�gration'
            bat 'mvn -Dtest="com.example.testingweb.integration.**" test'
            echo 'Fin des tests d\'int�gration'
          }
        }

      }
    }

  }
}