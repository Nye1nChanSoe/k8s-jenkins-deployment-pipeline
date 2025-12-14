pipeline {
    agent any

    environment {
        KUBE_SERVER = "https://kubernetes:6443"
        KUBE_TOKEN  = "k8s-jenkins-token"
    }

    stages {
        stage("Deploy to Kubernetes") {
            steps {
                withKubeConfig(
                    credentialsId: env.KUBE_TOKEN,
                    serverUrl: env.KUBE_SERVER
                ) {
                    sh '''
                      kubectl apply -f k8s/myapp.yaml
                      kubectl get pod myapp
                    '''
                }
            }
        }
    }
}
