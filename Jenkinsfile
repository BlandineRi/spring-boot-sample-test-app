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

  }
}