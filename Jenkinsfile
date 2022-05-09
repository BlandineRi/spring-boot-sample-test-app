pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'La construction va dÃƒÆ’Ã†â€™Ãƒâ€ Ã¢â‚¬â„¢ÃƒÆ’Ã¢â‚¬Å¡Ãƒâ€šÃ‚Â©marrer'
        bat 'mvn -Dskiptests clean package'
        echo 'Construction terminÃƒÆ’Ã†â€™Ãƒâ€šÃ‚Â©e'
        archiveArtifacts '**/target/*.jar'
      }
    }

    stage('Test') {
      parallel {
        stage('Unit') {
          steps {
            echo 'DÃƒÆ’Ã‚Â©marrage des tests unitaires'
            bat 'mvn -Dtest="com.example.testingweb.smoke.**" test'
            echo 'Fin des tests unitaires'
            junit '**/target/surefire-reports/TEST-*.xml'
          }
        }

        stage('Integration') {
          steps {
            echo 'DÃƒÂ©but de l\'intÃƒÂ©gration'
            bat 'mvn -Dtest="com.example.testingweb.integration.**" test'
            echo 'Fin des tests d\'intÃƒÂ©gration'
          }
        }

        stage('Functional') {
          steps {
            echo 'DÃ©but des tests fonctionnels'
            bat 'mvn -Dtest="com.example.testingweb.functional.**" test'
            echo 'Fin des tests fonctionnels'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Début du déploiement'
        bat 'mvn -B -DskipTests install'
        echo 'Fin du déploiement'
      }
    }

  }
}