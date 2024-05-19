Se construirá un pipeline que se encargue del proceso de automatización de la construcción del DockerFile. El pipeline se debe encargar de tomar el código de la aplicación, construir una
imagen, levantar un contenedor y subir esa imagen a DockerHub.
I Parte:
El JenkinsFile incluye la construcción de la imagen, ejecución de un contenedor usando esa imagen y publicación de esa imagen en un repositorio de imágenes (docker hub).
Componentes adicionales: Hadolint + Testing.
NOTA: Todo lo que sea relacionado a la administración de credenciales se debe gestionar de una forma segura, en vez de utilizar los valores directamente en texto plano en el pipeline. En este caso se utilizó variables para el user/pass de docker hub (export).
II Parte:
Utilizar Github Actions para la construcción de la imagen, ejecución de un contenedor usando esa imagen y publicación de esa imagen en un repositorio de imágenes (docker hub).
Componentes adicionales: Hadolint + Testing.
NOTA: Todo lo que sea relacionado a la administración de credenciales se debe gestionar de una forma segura, en vez de utilizar los valores directamente en texto plano en el pipeline. En este caso se declararon las variables secretas en Actions secrets.
