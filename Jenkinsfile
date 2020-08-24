pipeline {
    agent {
        label 'master'
    }
    parameters {
        string(name: 'BRANCH_PASSED_OVER', defaultValue: '${env.BRANCH_NAME}', description: 'pass branch value')
        string(name: 'PERSON2', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    }
    stages {
        stage('Build downstream'){
            steps {
                build job: 'jenkins-projectB/' + env.BRANCH_NAME.replaceAll("/", "%2F"), wait: false, parameters: [string(name: 'PERSON2', value: params.PERSON2), string(name: 'PASS_BRANCH_NAME', value: env.BRANCH_NAME)]
            }
        }
        stage('Build - Test') {
            steps {
                echo 'Create Artifact'
                script {
                    sh 'ping www.google.com -c 5'
                }
            }
        }
    }
}
