pipeline{
    // Directives 
    agent any
    tools {
        maven 'maven'
    }
    environment{
        ArtifactId = readMavenPom().getArtifactId()
        Version = readMavenPom().getVersion()
        Name = readMavenPom().getName()
        GroupId = readMavenPom().getGroupId()

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
                nexusArtifactUploader artifacts: [[artifactId: "${ArtifactId}", 
                classifier: '', 
                file: 'target/VinayDevOpsLab-0.0.3-SNAPSHOT.war', 
                type: 'war']], 
                credentialsId: '305c149f-d4a2-4219-a2b8-690661e73241', 
                groupId: "${GroupId}", 
                nexusUrl: '172.20.0.234:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'VinaysDevOpsLab-SNAPSHOT', 
                version: "${Version}'"
            }
        }

        // Stage 4. : Print Variable Pom information
        stage ('Print environment variables'){
            steps{
                echo "Artifact ID is '${ArtifactId}'"
                echo "Version ID is '${Version}'"
                echo "Group ID is '${GroupId}' "
                echo "Name is '${Name}'"
            }
        }


        // Stage 5. : Deploying
        stage ('Deploy'){
            steps {
                echo ' Deploying.....'
            }
        }
    }
}