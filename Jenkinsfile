node('Linux_1') {
    try {
        stage('Checkout') {
            checkout scm
        }
        
        stage('Build') {
            
            sh 'echo "Building Project"'
            def buildImage = docker.image("node:10-alpine")            
            buildImage.pull()
            buildImage.inside("-u root") {
                    sh 'yarn'
                    sh 'yarn build'
            }
        }
            

    }catch(e){
        currentBuild.result = 'FAILED'
        throw e
    }
}
