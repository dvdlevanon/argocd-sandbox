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
        dockerTags = sightd.getImageTags(env.GIT_COMMIT, subenvName)
    }
    
    stages {
        stage('Push Container') {
            steps {
                script {
                    for (tag in dockerTags) {
                        print tag
                    }
                }
            }
        }
    }
}