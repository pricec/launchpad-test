pipeline {
    agent any

    stages {
        stage("Apply") {
            steps {
                withCredentials([usernamePassword(credentialsId: 'common-dockerhub-up', usernameVariable: 'HUB_USER', passwordVariable: 'HUB_PASS')]) {
                    sh "docker login -u ${HUB_USER} -p ${HUB_PASS}"
                }
                sh "pwd && ls"
                sh 'docker run --rm -i -v $(pwd)/user.yaml:/root/.mirantis-launchpad/user.yaml -v $(pwd):/w -w /w mirantiseng/launchpad:latest apply'
            }
        }
    }
}
