pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'La construction va démarrer'
        bat 'mvn -Dskiptests clean package'
        echo 'Construction termin�e'
      }
    }

  }
}