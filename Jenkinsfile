node (label: 'linux-node') {
    checkout scm
    def nodeImage = docker.build("node:${env.BUILD_ID}")
    
    // Check if node container is already running
    def isRunning = sh(script: "docker ps | grep testnode", returnStatus:true)
    if (isRunning) {
        sh 'docker stop node'
        sh 'docker rm node'
    }

    // Run container
    sh "docker run -d --name node -p 3000:3000 ${nodeImage.imageName()}"
}
