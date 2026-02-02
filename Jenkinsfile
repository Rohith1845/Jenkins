pipeline {
    agent {
        node{
            label 'Agent-1'
        }
    }
    environment {
        COURSE="jenkins"
    }
    options {
        timeout(time: 10, unit: 'minutes')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Build'){
            steps{
                script{
                    sh """
                    echo "building"
                    echo "$COURSE"
                    #sleep 10
                    env
                    """
                }
            }
        }
        stage('Test'){
            steps{
                echo "testing"
            }
        }
        stage('Deploy'){
            steps{
                echo "deploying"
            }
        }
    }
    post {
        always {
            echo "I'm the end"
            cleanWs()
        }
        success{
            echo    "Im the success"
        }
        failure{
            echo    "im the failure"
        }
    }
}