pipeline {
    agent any
    tools {
        maven 'maven399'
    }
    environment {
        MAVEN_OPTS = '-Xmx2048m'
    }
    parameters {
        choice(name: 'MAVEN_COMMAND', choices: ['install', 'package', 'clean', 'test'], description: 'Select the Maven command to execute', defaultValue: 'install')
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello, World!'
            }
        }
        // stage('Source') {
        //     steps {
        //         echo 'Fetching source code from GitHub'
        //         git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
        //     }
        // }
        stage('Execute Maven Command') {
            steps {
                echo "Running mvn ${params.MAVEN_COMMAND}"
                sh "mvn ${params.MAVEN_COMMAND} -X"
            }
        }
        // stage('Build') {
        //     steps {
        //         echo 'Running mvn install'
        //         sh 'mvn install -X'
        //     }
        // }
        stage('Parallel Build and Test') {
            parallel {
                stage('Package') {
                    steps {
                        echo 'Running mvn package'
                        // sh 'mvn package'
                    }
                }
                stage('Test') {
                    steps {
                        echo 'Running mvn test'
                        // sh 'mvn test'
                    }
                }
            }
        }
    }
}
