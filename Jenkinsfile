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

    stage('Docker image') {
      steps {
        sh '''
# Build Docker Image 
docker build -t index.html:latest 

# Del of old image
docker rmi registry.me:5000/mysiteweb:latest

# Upload to the local registry
docker tag mysiteweb:latest registry.me:5000/mysiteweb:latest 
docker push registry.me:5000/mysiteweb:latest
'''
      }
    }

    stage('Launch web site') {
      steps {
        sh '''# Run docker website
docker run --name mywebsite -d -p 80:80 registry.me:5000/mysiteweb:latest'''
      }
    }

  }
}