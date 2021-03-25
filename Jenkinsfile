pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent {
        label 'all'
    }
    stages {
        stage('build and push') {
            when {
                branch 'master'
            }
            sh "docker build -t docker/getting-started ."

            steps {
                withDockerRegistry([url: "", credentialsId: "https://hub.docker.com/repository/docker/ferencmolnar/jenkins-docker"]) {
                    sh("docker push docker/jenkins-docker")
                }
            }
        }
    }
}
