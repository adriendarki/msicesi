pipeline {
  agent any
  stages {
    stage('creadockerFile') {
      steps {
        sh '''# Creation du Dockerfile
touch Dockerfile



# Renseignement du Dockerfile
echo "FROM nginx:alpine
COPY index.html /usr/share/nginx/html
" >> Dockerfile



echo "Check dockerfile"
cat Dockerfile



echo ""
echo "Check index.html"
cat index.html'''
      }
    }

  }
}