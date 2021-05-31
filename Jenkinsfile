// Uses Declarative syntax to run commands inside a container.
pipeline {
    agent {
        kubernetes {
            // Rather than inline YAML, in a multibranch Pipeline you could use: yamlFile 'jenkins-pod.yaml'
            // Or, to avoid YAML:
            // containerTemplate {
            //     name 'shell'
            //     image 'ubuntu'
            //     command 'sleep'
            //     args 'infinity'
            // }
            yaml '''
apiVersion: v1
kind: Pod
metadata:
  name: pod-name
spec:
  containers:
  - name: gcloud
    image: python:3
    command: ['sh', '-c', 'echo "Hello, Kubernetes!" && sleep 3600']
    # The pod template ends here

'''
            // Can also wrap individual steps:
            // container('shell') {
            //     sh 'hostname'
            // }
            //defaultContainer 'shell'
        }
    }
    stages {
        stage('Main') {
            steps {
                sh 'hostname'
                sh 'python --version'
            }
        }
    }
}
