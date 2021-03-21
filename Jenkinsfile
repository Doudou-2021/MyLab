pipeline{
    // Directives 
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // Stage 1. Build
        stage ('Build'){
            steps {
                sh 'mv clean install package'
            }
        }

        // Stage 2. : Testing
        stage ('Test'){
            steps {
                echo ' testing.....'
            }
        }

        // Stage 3. : Deploying
        stage ('Deploy'){
            steps {
                echo ' Deploying.....'
            }
        }
    }
}