pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'La construction va dÃƒÆ’Ã†â€™Ãƒâ€šÃ‚Â©marrer'
        bat 'mvn -Dskiptests clean package'
        echo 'Construction terminÃƒÆ’Ã‚Â©e'
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'DÃƒÂ©marrage des tests unitaires'
            bat 'mvn -Dtest="com.example.testingweb.smoke.**" test'
            echo 'Fin des tests unitaires'
          }
        }

        stage('Integration') {
          steps {
            echo 'DÃ©but de l\'intÃ©gration'
            bat 'mvn -Dtest="com.example.testingweb.integration.**" test'
            echo 'Fin des tests d\'intÃ©gration'
          }
        }

        stage('Functional') {
          steps {
            echo 'Début des tests fonctionnels'
            bat 'mvn -Dtest="com.example.testingweb.functional.**" test'
            echo 'Fin des tests fonctionnels'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'D�but du d�ploiement'
        bat 'mvn -B -DskipTests install'
        echo 'Fin du d�ploiement'
      }
    }

  }
}