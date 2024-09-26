node (label: 'linux-node') {
    checkout scm
    def nodeImage = docker.build("node:${env.BUILD_ID}")
    def nodeContainerName = "node"
    
    // Check if node container is already running
    def isRunning = sh(script: "docker ps | grep ${nodeContainerName}", returnStatus:true)
    if (!isRunning) {
        sh "docker stop ${nodeContainerName}"
        sh "docker rm ${nodeContainerName}"
    }

    // Run container
    sh "docker run -d --name ${nodeContainerName} -p 3000:3000 ${nodeImage.imageName()}"
}
