pipeline {
    agent any
    // triggers {
    //     pollSCM ('* * * * *')
    // }
    stages {
        stage('SCM') {
            steps {
                git branch: 'main',
                url: 'https://github.com/shashikamle99/taxi-booking-app.git'
            }
        }
        stage('Build package') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('SonarQube Analysis') {
          steps {
              withSonarQubeEnv('SONAR_CLOUD') {
                sh "mvn sonar:sonar -Dsonar.projectKey=taxi-booking -Dsonar.organization=java-project-demo -Dsonar.token=a64e938e4479814e8dd3a080e2b085270f7d884b"
                }
            } 
        }
    } 
}       