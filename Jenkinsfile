#!/usr/bin/env groovy

node {
    stage ('Preparation') {
        echo 'Cloning repo...'
        git credentialsId: '480beb66-2115-44cc-b64f-8d77e6efbdc5', url: 'git@github.com:magnubac/ca-project.git'
    }
    stage ('Build docker image') {
        sh 'docker build -t magnubac/ca_project_image:1.0 .'
    }
    stage ('Run unittests') {
        sh 'docker run --rm magnubac/ca_project_image:1.0 python tests.py'
    }
    stage ('Stop prev version') {
        try {
            sh 'docker stop ca_project_container'
            sh 'docker rm ca_project_container'
        } catch (Exception ex) {
            echo 'Could not stop previous version.'
        }
    }
    stage ('Run run.py') {
        sh 'docker run --name ca_project_container -d -p 5000:5000 magnubac/ca_project_image:1.0'
    }
    stage ('Functional test') {
        sh 'curl http://52.31.226.107:5000/'
    }
}
