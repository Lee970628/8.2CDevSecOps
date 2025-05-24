pipeline {
agent any

environment {
    PATH = "/Users/liiiii/.nvm/versions/node/v22.8.0/bin:/opt/homebrew/opt/openjdk@17/bin:${env.PATH}"
    JAVA_HOME = "/opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk/Contents/Home"
    SONAR_SCANNER_HOME = "/Users/liiiii/Desktop/SIT753 PPIT/wk8/nodejs-goof/sonar-scanner-4.8.0.2856"
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
stage('SonarCloud Analysis') {
steps {
withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
sh '''
echo "Starting SonarCloud Analysis with real SonarScanner..."
echo "Project Key: Lee970628_8.2CDevSecOps"
echo "Organization: lee970628"
echo "SonarScanner Home: $SONAR_SCANNER_HOME"

# Add SonarScanner to PATH
export PATH="$SONAR_SCANNER_HOME/bin:$PATH"

# Run SonarScanner
sonar-scanner \
  -Dsonar.projectKey=Lee970628_8.2CDevSecOps \
  -Dsonar.organization=lee970628 \
  -Dsonar.sources=. \
  -Dsonar.host.url=https://sonarcloud.io \
  -Dsonar.login=$SONAR_TOKEN \
  -Dsonar.exclusions=node_modules/**,test/**,sonar-scanner-4.8.0.2856/**,*.zip

echo "SonarCloud Analysis completed!"
'''
}
}
}
stage('NPM Audit (Security Scan)') {
steps {
sh 'npm audit || true'
}
}
}

post {
always {
echo '''

}
success {
echo "Complete DevSecOps pipeline with real SonarCloud analysis successful!"
}
failure {
echo "Pipeline failed - check logs for details"
}
}
}
