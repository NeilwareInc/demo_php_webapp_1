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
                sh "docker-compose up -d"
            }
        }
        
        stage("Backup to DockerHub") {
            steps {
                sh "docker tag php-web-app1:newest florenceomoruyi/php-web-app1:${env.IMAGE_TAG}"
                sh "docker push florenceomoruyi/php-web-app1:${env.IMAGE_TAG}"
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

