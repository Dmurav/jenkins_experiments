pipeline {
    agent any
    stages {
        stage("Build Maven") {
            steps {
                git 'https://github.com/Dmurav/gatling_genkins.git'
                sh 'mvn -B clean package'
            }
        }
        stage("Run Gatling") {
            steps {
                sh 'mvn gatling:test'
            }
            post {
                always {
                    gatlingArchive()
                }
            }
        }
    }
}
