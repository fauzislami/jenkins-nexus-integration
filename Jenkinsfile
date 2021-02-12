pipeline {
    agent any

    tools {
        maven 'maven'
        jdk 'jdk8'
    }

    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "192.168.1.116:8081"
        NEXUS_REPOSITORY = "maven-nexus-repo"
        NEXUS_CREDENTIAL_ID = "nexus-user-credentials"

        //sesuaikan dengan aplikasi
        APPLICATION_NAME = "springtest"
        VERSION = "1"
    }

    stages {
        stage('Building code') {
            steps {
                sh './testenv.sh'
                sh 'mvn clean compile'
            }
        }

        stage('Unit testing') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                     catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                         junit 'target/surefire-reports/*.xml'
                         sh 'mvn package'
                     }
                }
            }
        }

        stage('Push artifact to Nexus') {
            steps {
                script {
                    pom = readMavenPom file: "pom.xml";
                    filesByGlob = findFiles(glob: "target/*.${pom.packaging}");
                    echo "${filesByGlob[0].name} ${filesByGlob[0].path} ${filesByGlob[0].directory} ${filesByGlob[0].length} ${filesByGlob[0].lastModified}"
                    artifactPath = filesByGlob[0].path;
                    artifactExists = fileExists artifactPath;
                    if(artifactExists) {
                        echo "*** File: ${artifactPath}, group: ${pom.groupId}, packaging: ${pom.packaging}, version ${pom.version}";
                        nexusArtifactUploader(
                            nexusVersion: NEXUS_VERSION,
                            protocol: NEXUS_PROTOCOL,
                            nexusUrl: NEXUS_URL,
                            groupId: pom.groupId,
                            version: pom.version,
                            repository: NEXUS_REPOSITORY,
                            credentialsId: NEXUS_CREDENTIAL_ID,
                            artifacts: [
                                [artifactId: pom.artifactId,
                                 classifier: '',
                                 file: artifactPath,
                                 type: pom.packaging],
                                 [artifactId: pom.artifactId,
                                  classifier: '',
                                  file: "pom.xml",
                                  type: "pom"]

                                ]
                        );
                    } else {
                        error "*** File: ${artifactPath}, could not be found";
                    }
                }
            }
        }

        stage('Build and Push Image ') {
            steps {
                script {
                    docker.withRegistry('192.168.1.116:5000', "$NEXUS_CREDENTIAL_ID") {
                        def customImage = docker.build("192.168.1.116:5000/image/springtest:$VERSION")
                            customImage.push()

                     }
                }
            }
            post {
                success {
                    sh 'docker rmi -f $(docker images -q)'
                }
            }
       }

    }
}
