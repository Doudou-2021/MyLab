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
                sh 'mvn clean install package'
            }
        }

        // Stage 2. : Testing
        stage ('Test'){
            steps {
                echo 'testing.....'
            }
        }

        // Stage 3. : Publish the artefacts to Nexus
        stage ('Publish to Nexus'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', 
                classifier: '', 
                file: 'target/VinayDevOpsLab-0.0.2-SNAPSHOT.war', 
                type: 'war']], 
                credentialsId: '305c149f-d4a2-4219-a2b8-690661e73241', 
                groupId: 'com.vinaysdevopslab', 
                nexusUrl: '172.20.0.234:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'VinaysDevOpsLab-SNAPSHOT', 
                version: '0.0.2-SNAPSHOT'
            }
        }

        // Stage 4. : Deploying
        stage ('Deploy'){
            steps {
                echo ' Deploying.....'
            }
        }
    }
}