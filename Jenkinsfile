pipeline {
    agent any
    // tools {
    //     maven 'maven399'
    // }
    // environment {
    //     MAVEN_OPTS = '-Xmx2048m'
    // }
    // parameters {
    //     choice(name: 'MAVEN_COMMAND', choices: ['install', 'package', 'clean', 'test'], description: 'Select the Maven command to execute')
    // }
    stages {
        // stage('Hello') {
        //     steps {
        //         echo 'Hello, World!'
        //     }
        // }
        // stage('Source') {
        //     steps {
        //         echo 'Fetching source code from GitHub'
        //         git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
        //     }
        // // }
        // stage('Execute Maven Command') {
        //     steps {
        //         echo "Running mvn ${params.MAVEN_COMMAND}"
        //         // sh "mvn ${params.MAVEN_COMMAND} -X"
        //     }
        // }
        // stage('Build') {
        //     steps {
        //         echo 'Running mvn install'
        //         sh 'mvn install -X'
        //     }
        // }
        // stage('Parallel Build and Test') {
        //     parallel {
        //         stage('Package') {
        //             steps {
        //                 echo 'Running mvn package'
        //                 // sh 'mvn package'
        //             }
        //         }
        //         stage('Test') {
        //             steps {
        //                 echo 'Running mvn test'
        //                 // sh 'mvn test'
        //             }
        //         }
        //     }
        // }

        stage('Deployment') {
            steps {
                script{
                    sshPublisher(publishers: [sshPublisherDesc(configName: 'Mazen', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'myscript.py')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                    sh "python myscript.py"
                }
            }
        }

        // stage('Deployment') {
        //     steps {
        //         script {
        //             // Transfer file to remote server
        //             sshPublisher(
        //                 publishers: [
        //                     sshPublisherDesc(
        //                         configName: 'Mazen',
        //                         transfers: [
        //                             sshTransfer(
        //                                 sourceFiles: 'myscript.py',
        //                                 remoteDirectory: '/target/directory',
        //                                 execCommand: 'python /target/directory/myscript.py'
        //                             )
        //                         ],
        //                         verbose: true
        //                     )
        //                 ]
        //             )
        //         }
        //     }
        //     post {
        //         failure {
        //             echo 'Deployment failed'
        //         }
        //     }
        // }
    }
}
