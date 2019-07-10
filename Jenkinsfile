node {
        stage("Checkout") {
            checkout scm
        }

        stage('Maven Build') {
            sh "mvn package"
        }

        stage('Docker image') {
             docker.build("membrane/msa-stock")
        }

        stage("Deploy") {
            sh "docker rm -f stock || echo 'ok'"
            sh "docker run -d --name stock --net shopnet -p 8081:8081 membrane/msa-stock"
        }
}
