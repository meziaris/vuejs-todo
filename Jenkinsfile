pipeline {
    
    agent any
        
    stages {
        stage('Sonarqube Analysis') {
            environment {
                scannerHome = tool 'SonarQubeScanner'
            }
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=vuejs"
                }
                // timeout(time: 10, unit: 'MINUTES') {
                //     waitForQualityGate abortPipeline: true
                // }
            }
        }
        // stage('Sonarqube Analysis'){
        //     steps {
        //         sh 'sonar-scanner -Dsonar.projectKey=vuejs-todo -Dsonar.sources=. -Dsonar.host.url=https://sonar.mezi.space -Dsonar.login=da96b4ffd33ac4b312ce133ae4d7deed0f4bc6e6'
        //     }
        // }
        // stage('Build Docker Image') {
        //     steps {
        //         sh 'docker build -t meziaris/gateway:$BUILD_NUMBER .'
        //     }
        // }
        // stage('Push Image to DockerHub') {
        //     steps {
		// 		sh 'docker push meziaris/gateway:$BUILD_NUMBER'
        //     }
        // }
        // stage('Deploy to Docker') {
        //     steps {
        //         checkout scm
        //         sh """
        //         sed -i 's/latest/$BUILD_NUMBER/g' docker-compose.yml
        //         docker-compose up -d
        //         """
        //     }
        // }
        // stage('Remove docker image last build Dev') {
        //     steps {
        //         sh 'docker rmi meziaris/gateway:$BUILD_NUMBER'
        //     }
        // }
        stage('Git') {
            steps {
                step([$class: 'WsCleanup'])
                checkout scm
            }
        }
    }
}