node (label: 'linux-node') {
    checkout scm
    def nodeImage = docker.build("my_node:${env.BUILD_ID}")
    sh "docker run -d --name my_node -p 3000:3000 ${nodeImage.imageName()}:${env.BUILD_ID}"
}
