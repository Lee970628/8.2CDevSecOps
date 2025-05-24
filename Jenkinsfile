pipeline {
agent any

environment {
    PATH = "/Users/liiiii/.nvm/versions/node/v22.8.0/bin:${env.PATH}"
}

stages {
stage('Checkout') {
steps {
git branch: 'main', url: ' https://github.com/Lee970628/8.2CDevSecOps.git'
}
}
stage('Install Dependencies') {
steps {
sh 'npm install'
}
}
stage('Run Tests') {
steps {
sh 'npm test || true'
}
}
stage('Generate Coverage Report') {
steps {
sh 'npm run coverage || true'
}
}
