pipeline{
    agent {
        label 'php_agent'
    }

    environment {
        IMAGE_TAG = "Default"
    }

    stages {
        stage("Deploy in Container") {
            steps {
                sh "docker-compose build"
                sh "docker-compose up -d --remove-orphans"
            }
        }
        
        stage("Backup to DockerHub") {
            steps {
                sh "docker tag demo_php_webapp_1:newest aovlabile/demo_php_webapp_1:${env.IMAGE_TAG}"
                sh "docker push aovlabile/demo_php_webapp_1:${env.IMAGE_TAG}"
            }
        }
    }
}

/*
Delete the old image(s)
Build the new image
Delete the old container
Run the new container(s): docker-compose up -d
Push new image to dockerhub
*/

