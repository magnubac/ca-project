#!/usr/bin/env groovy

node {
    stage ('Preparation') {
        echo 'Cloning repo...'
        git credentialsId: '480beb66-2115-44cc-b64f-8d77e6efbdc5', url: 'git@github.com:magnubac/ca-project.git'
    }
    stage ('Run unittests') {
        sh 'cd ca-project'
        sh 'python tests.py'
    }
}
