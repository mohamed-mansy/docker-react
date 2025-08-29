pipeline {
    agent {
        label 'docker'
    }

    stages{
        stage('build from a docker file'){
            steps {
                script {
                    sh 'docker build -t moka/docker-react -f Dockerfile.dev .'
                }
            }
        }

        stage('run those test'){
            steps {
                script {

                    env.DOCKER_BUILDKIT = 1
                    sh 'docker run -e CI=true moka/docker-react npm run test'
                    }
            }
        }
    }
}