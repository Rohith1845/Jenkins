pipeline {
    // This are pre-build steps
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
        booleanParam(name: 'Deploy', defaultValue: false, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    // This are Build steps
    stages {
        stage('Build'){
            steps{
                script{
                    sh """
                    echo "building"
                    echo "$COURSE"
                    sleep 10

                    echo "Hello ${params.PERSON}"
                    echo "Biography: ${params.BIOGRAPHY}"
                    echo "Toggle: ${params.TOGGLE}"
                    echo "Choice: ${params.CHOICE}"
                    echo "Password: ${params.PASSWORD}"

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
            // This used for approval like terraform apply situation
            // input {
            //     message "Should we continue?"
            //     ok "Yes, we should."
            //     submitter "alice,bob"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            // When is used to not run the stage
            when { 
                expression { $param.Deploy }

            }
            steps{
                script{
                    sh """
                        echo "deploying"
                    """
                }
                
            }
        }
    }
    // This are post build steps
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