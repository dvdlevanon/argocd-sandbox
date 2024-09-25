pipeline {
    agent any
    
    options {
        ansiColor('xterm')
        disableConcurrentBuilds()
    }
    
    triggers {
        pollSCM '* * * * *'
    }
    
    environment {
        dashboardImage = null
        
        subenvName = sightd.getSubenvNameFromBranch()
    }
    
    stages {
        stage('Push Container') {
            steps {
                script {
                    dockerTags = sightd.getImageTags(env.GIT_COMMIT, subenvName)
                    
                    for (tag in dockerTags) {
                        print tag
                    }
                }
            }
        }
    }
}
