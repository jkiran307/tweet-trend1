pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    environment {
        PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
    }

    stages {
        stage('build') {
            steps {
                sh 'mvn clean deploy -X -DskipTests'
            //    git branch: 'main', url: 'https://github.com/ravdy/tweet-trend-new.git'
            }
        }
        stage('SonarQube analysis') {
        environment {
          scannerHome = tool 'jkiran307-sonar-scanner';
        }
        steps {
        withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
        sh "${scannerHome}/bin/sonar-scanner"
    }
        }
  }
    }
}
