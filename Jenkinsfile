#!/usr/bin/env groovy

node {
    stage ('Preparation') {
        echo 'Cloning repo...'
        git credentialsId: '480beb66-2115-44cc-b64f-8d77e6efbdc5', url: 'git@github.com:magnubac/ca-project.git'
    }
    stage ('Build docker image') {
        sh 'docker build -t ca_project_image:1.0 .'
    }
    stage ('Run unittests') {
        sh 'docker run --rm ca_project_image:1.0 python tests.py'
    }
}
