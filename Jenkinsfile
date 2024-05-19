pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Clonar el repositorio
                    // sh 'git clone https://github.com/rduserjob/pipeline.git'
                    //Instalamos Hadolint para chequear la imagen
                    sh 'docker pull hadolint/hadolint'
                    // Construir la imagen Docker
                    sh 'ls -l && pwd'
                    sh 'docker build -f /var/lib/jenkins/workspace/deploymentdocker-mimi-des13/nginx -t nginx_des13 .'
                    //Chequear la imagen creada
                    sh 'docker images'
                    // Chequear con Hadolint
                    sh 'docker run --rm -i hadolint/hadolint < /var/lib/jenkins/workspace/deploymentdocker-mimi-des13/nginx' 
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    // Levantar el contenedor
                    sh 'docker run -d --name my-app-container nginx'
                    //chequear que el contenedor este corriendo
                    sh'docker  ps'
                    // Para Testear el correcto funcionamiento
                    //sh'curl localhost:8083'
                }
            }
        }
        stage('Push Image to DockerHub') {
            steps {
                script {
                    // Iniciar sesión en DockerHub
                    sh 'docker login -u romitelli -p MsRr.21119723'
                    // Etiquetar la imagen
                    sh 'docker tag nginx_des13 romitelli/nginxdesafio13'
                    // Subir la imagen a DockerHub
                    sh ' docker push $user/nginxdesafio13'
                }
            }
        }
    }
}
