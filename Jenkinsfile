pipeline {
    agent any

    environment {
        KUBE_SERVER = "https://kubernetes:6443"
        KUBE_TOKEN  = "eyJhbGciOiJSUzI1NiIsImtpZCI6Ii1GcFZueHRlMHYtb3V6bzdleElJTVgwcmVvcHR3SVRFMnRkeV9IWFY3QkEifQ.eyJhdWQiOlsiaHR0cHM6Ly9rdWJlcm5ldGVzLmRlZmF1bHQuc3ZjLmNsdXN0ZXIubG9jYWwiLCJrM3MiXSwiZXhwIjoxNzY1NzM5MDk3LCJpYXQiOjE3NjU3MzU0OTcsImlzcyI6Imh0dHBzOi8va3ViZXJuZXRlcy5kZWZhdWx0LnN2Yy5jbHVzdGVyLmxvY2FsIiwianRpIjoiMjUwNDAyYjQtZDg1MS00N2Y3LTg1ODMtYmNjZTkwYTkwYWU4Iiwia3ViZXJuZXRlcy5pbyI6eyJuYW1lc3BhY2UiOiJkZWZhdWx0Iiwic2VydmljZWFjY291bnQiOnsibmFtZSI6ImplbmtpbnMtcm9ib3QiLCJ1aWQiOiI2MzQ1MTg3NC1iYTVmLTRmMjYtYjQ4Ny01MmMwMDNmYWViMTEifX0sIm5iZiI6MTc2NTczNTQ5Nywic3ViIjoic3lzdGVtOnNlcnZpY2VhY2NvdW50OmRlZmF1bHQ6amVua2lucy1yb2JvdCJ9.S5eubciBWME8hNrwCZwEWzICB1U4PGK7fQe4nuhFoAlU0dvZIB0B636NJtrLXAnpwcVklsn36yFgOUenK9QCnYZPzkxdxH8IWL0jm-LyNL2ceEjFKCdMvYAm11zi326BrcPh73ugqLvCyZ1S0u1_mI8tC5MCQxblMfknoPbrQsozqtaG5rZwTAb7H9zwAJYxVGNsfSVIJI5rEJ7MjIB3yovVM8m7PpiowCwZbVYt-QswkRRZgFiKXYUIIZTANG1Cxy7LjbUWOqlsFGVZfiPRMH5W0IFyuytZvY5swFbo8W1ndJS4EyDosA2oWrkr8RViPXCtkH02hdawd6a2QX1bpA"
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
