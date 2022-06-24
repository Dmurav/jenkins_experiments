pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
        git "GIT"
    }
    stages {
        stage("Build") {
            steps {
                git branch: 'main', credentialsId: 'github_credentials', url: 'https://github.com/Dmurav/gatling_genkins.git'
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
