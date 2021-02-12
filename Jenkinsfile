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
        QUAY_CREDENTIAL_ID = "quay"
        OCP_DEV = "dev"
        OCP_SIM = "sim"
        OCP_PROD = "prod"
        TOKEN_DEV = "eyJhbGciOiJSUzI1NiIsImtpZCI6IjhTMGl4SVEtX0c5dFV1RHpSc0ItaWl2bTNJekVqZUlqX2RJekFEZXpKV3MifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZXYiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlY3JldC5uYW1lIjoiamVua2lucy10b2tlbi1wMnBxdiIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50Lm5hbWUiOiJqZW5raW5zIiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQudWlkIjoiZWViNTQ1OWQtNWMxZC00MzliLWE0NjMtZDBhOGMyNGZjOTQ2Iiwic3ViIjoic3lzdGVtOnNlcnZpY2VhY2NvdW50OmRldjpqZW5raW5zIn0.jOsugc-L7IOsTy9S333OjoEgh_QcPyRO8dVm9EeznccymnAzkN6q5HlZzq-31O-Bnvs_C0-LCdiulbKUs0ubTmMZRixvWoZP2ddpZ8fjX6uNRbCYE_6x1WSa7v7dlakiZf5rvBlcLNeK7-q5XBFxvAyNrqPmLBDzSAJE4XkOagCOpuk3VnQqjVECrF-utBk0QWaitarXT5liYImfpC-NXth_We0dtwgOzjRdRpE2Ov0fvUxhiQZdSdXUg6chuxUi-_M1g5ahI3apOUDSWYEqmDftnGKQQpVtziyUQUt7zgf3TK5bo50HScvRYallBPjahEsT42Aq5NTfdTq9FlIrCg"
        TOKEN_SIM = "eyJhbGciOiJSUzI1NiIsImtpZCI6IjhTMGl4SVEtX0c5dFV1RHpSc0ItaWl2bTNJekVqZUlqX2RJekFEZXpKV3MifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJzaW0iLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlY3JldC5uYW1lIjoiamVua2lucy10b2tlbi1iZ3dsayIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50Lm5hbWUiOiJqZW5raW5zIiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQudWlkIjoiOWUxMTFhNTctNDQ0ZC00MzgxLTg3OTYtNDg5M2Y4OGI1NmFkIiwic3ViIjoic3lzdGVtOnNlcnZpY2VhY2NvdW50OnNpbTpqZW5raW5zIn0.Oi4oAsyCzWOXE0JkH5SO5lS6qqNcs0-QTiBDOztyynL3iWuIvBnVB6oPTjJhaFolAAu7iUrFBfilOqLXRDtulrwSm0MAjzarz1XjY6exT-Hgwz12UIGn9lBOd6nNC-QTOuLuotZ0-c7q93p5xCPfk1--2ByfaNH1sIe2zL5dsSuc6N-rgVyNfD0PCuoX2uvF_0BVO9Pv07ONl3RQtTvOYlMH4ukCO45hXXv1nnN-1VG66a4Z73qGXDHEfYp5KKN3bLf3Dew3gA8-F-h9suQL3VLkrlWO-o0WF79cGx9aVB7R0wyGH24d9dw6HsWp5qA_ZFg6dAA-9uklfmIA4DClxg"
        TOKEN_PROD = "eyJhbGciOiJSUzI1NiIsImtpZCI6IjhTMGl4SVEtX0c5dFV1RHpSc0ItaWl2bTNJekVqZUlqX2RJekFEZXpKV3MifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJwcm9kIiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImplbmtpbnMtdG9rZW4tdmdydmwiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC5uYW1lIjoiamVua2lucyIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50LnVpZCI6IjAyMGI5NmZmLTNjNWYtNDcwYy05NTM1LTYxM2IxYjBiYTBhZSIsInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDpwcm9kOmplbmtpbnMifQ.bsX4ChzpsuMtE2IWvJ9Q6wQA8--IMTl0rVhBrdfNgmv01fmE61pu3MVXYPqgGZ9PKmGoiwgTYOj30xaBnem7RPx2vBEpzaparknO1S456_rr6gUMiMtPjKT3LNbWh_z-OKdKglxidthQ1J2TZ08Z_GTWVJIKVLtVQKRmXnKAyXe_AkN99U4jb_IAg4vJR4TimAGJq_ZOroi_-QmQDQwVlV35ol6rveOAsgHL24Q47YUESceVs1dxRpWoui-01GY8Z9UMQqFxqJsozAkgCdHL9uK6kDYobCS3WQfng3_lAS-5itXzlm5-899JBs4tbEn9ZDzuiCLCoHtqA9Sba1-1pA"


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
            post {
                success {
                    script{
                        withEnv(['JIRA_SITE=jira']) {
                            def comment = [ body: 'Build success' ]
                            jiraAddComment idOrKey: 'CT-1', input: comment
                        }
                    }
                }
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
                    docker.withRegistry('https://quay.io', "$QUAY_CREDENTIAL_ID") {
                        def customImage = docker.build("quay.io/fauzislami/$OCP_DEV-$APPLICATION_NAME:$VERSION")
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

        stage('Deploy to OCP-Dev') {
            when {
                expression {
                    openshift.withCluster('ocp-dev') {
                        return !openshift.selector('deployment', '"$OCP_DEV"-"$APPLICATION_NAME"').exists()
                    }
                }
            }
            steps {
                    script {
                    openshift.withCluster( 'ocp-dev' ) {
                        openshift.withProject( 'dev' ) {
                            def app = openshift.newApp('quay.io/fauzislami/$OCP_DEV-$APPLICATION_NAME:1', '--name="$OCP_DEV"-"$APPLICATION_NAME"')
                            echo "new app created ${app.count()} objects named: ${app.names()}"
                            app.describe()
                            
                            echo "Hello from project ${openshift.project()} in cluster ${openshift.cluster()}"
                            }
                        }   
                    
                }
            }
        }

        stage('Expose Route in OCP-Dev') {
            when {
                expression {
                    openshift.withCluster('ocp-dev') {
                        return !openshift.selector('route', '"$OCP_DEV"-"$APPLICATION_NAME"').exists()
                    }
                }
            }
            steps {
                script{
                    openshift.withCluster('ocp-dev') {
                        openshift.withProject('dev') {
                            openshift.selector('service', '"$OCP_DEV"-"$APPLICATION_NAME"').expose()
                            // sh '''
                            // oc login --token $TOKEN_DEV
                            // oc expose service/"$OCP_DEV"-"$APPLICATION_NAME"
                            // '''
                        }
                    }
                }
            }
        }

        stage('Rollout Deployment in OCP-Dev') {
            steps {
                script {
                    sh '''
                    oc login --token $TOKEN_DEV
                    oc rollout restart deployment/"$OCP_DEV"-"$APPLICATION_NAME"
                    '''
                }
            }
        } 

        stage('Approval deployment to OCP-Sim') {
            steps {
                script {
                    input 'Promote deployment to OCP-Sim ?'
                }
            }
        }

                stage('Deploy to OCP-Sim') {
            when {
                expression {
                    openshift.withCluster('ocp-sim') {
                        return !openshift.selector('deployment', '"$OCP_SIM"-"$APPLICATION_NAME"').exists()
                    }
                }
            }
            steps {
                    script {
                    openshift.withCluster( 'ocp-sim' ) {
                        openshift.withProject( 'sim' ) {
                            def app = openshift.newApp('quay.io/fauzislami/$OCP_DEV-$APPLICATION_NAME:1', '--name="$OCP_SIM"-"$APPLICATION_NAME"')
                            echo "new app created ${app.count()} objects named: ${app.names()}"
                            app.describe()
                            
                            echo "Hello from project ${openshift.project()} in cluster ${openshift.cluster()}"
                            }
                        }   
                    
                }
            }
        }

        stage('Expose Route in OCP-Sim') {
            when {
                expression {
                    openshift.withCluster('ocp-sim') {
                        return !openshift.selector('route', '"$OCP_SIM"-"$APPLICATION_NAME"').exists()
                    }
                }
            }
            steps {
                script{
                    openshift.withCluster('ocp-sim') {
                        openshift.withProject('sim') {
                            openshift.selector('service', '"$OCP_SIM"-"$APPLICATION_NAME"').expose()
                            // sh '''
                            // oc login --token $TOKEN_SIM
                            // oc expose service/"$OCP_SIM"-"$APPLICATION_NAME"
                            // '''
                        }
                    }
                }
            }
        }

        stage('Rollout Deployment in OCP-Sim') {
            steps {
                script {
                    sh '''
                    oc login --token $TOKEN_SIM
                    oc rollout restart deployment/"$OCP_SIM"-"$APPLICATION_NAME"
                    '''
                }
            }
        } 

        stage('Approval deployment to OCP-Prod') {
            steps {
                script {
                    input 'Promote deployment to OCP-Prod ?'
                }
            }
        }

        stage('Deploy to OCP-Prod') {
            when {
                expression {
                    openshift.withCluster('ocp-prod') {
                        return !openshift.selector('deployment', '"$OCP_PROD"-"$APPLICATION_NAME"').exists()
                    }
                }
            }
            steps {
                    script {
                    openshift.withCluster( 'ocp-prod' ) {
                        openshift.withProject( 'prod' ) {
                            def app = openshift.newApp('quay.io/fauzislami/$OCP_DEV-$APPLICATION_NAME:1', '--name="$OCP_PROD"-"$APPLICATION_NAME"')
                            echo "new app created ${app.count()} objects named: ${app.names()}"
                            app.describe()
                            
                            echo "Hello from project ${openshift.project()} in cluster ${openshift.cluster()}"
                            }
                        }   
                    
                }
            }
        }

        stage('Expose Route in OCP-Prod') {
            when {
                expression {
                    openshift.withCluster('ocp-prod') {
                        return !openshift.selector('route', '"$OCP_PROD"-"$APPLICATION_NAME"').exists()
                    }
                }
            }
            steps {
                script{
                    openshift.withCluster('ocp-prod') {
                        openshift.withProject('prod') {
                            openshift.selector('service', '"$OCP_PROD"-"$APPLICATION_NAME"').expose()
                            // sh '''
                            // oc login --token $TOKEN_PROD
                            // oc expose service/"$OCP_PROD"-"$APPLICATION_NAME"
                            // '''
                        }
                    }
                }
            }
        }

        stage('Rollout Deployment in OCP-Prod') {
            steps {
                script {
                    sh '''
                    oc login --token $TOKEN_PROD
                    oc rollout restart deployment/"$OCP_PROD"-"$APPLICATION_NAME"
                    '''
                }
            }
        } 
    }
}
