node {
    try {
        def app
    
        stage('Clone repository') {
            checkout scm
        }
    
        stage('Build image') {
            app = docker.build('f4biogr/example-app')
        }

        stage('Test') {
            app.inside {
                sh 'npm test'
            }
        }
    
<<<<<<< HEAD
        stage('Push image') {
            docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                app.push('latest')
            }
        }
    } catch(error) {
        withCredentials([[$class: 'StringBinding', credentialsId: 'slack-webhook-url', variable: 'SLACK_URL']]) {
            sh "curl -XPOST -d 'playload={ \"color\": \"danger\", \"text\": \":warning: Build failed: $error (see <${env.BUILD_URL}/console|the build logs>)\"}' ${env.SLACK_URL}"
=======
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BRANCH_NAME}-latest")
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
>>>>>>> 5ea6476833b0b0d70cc8092dcb823d07781edd3e
        }
    }
}