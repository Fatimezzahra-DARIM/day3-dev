pipeline {
agent any
tools {
maven 'Maven'
}
environment{
SONAR_URL="http://URL_SONAR:9000"
}
stages {
stage("Source") {
steps {
git branch: 'main', credentialsId: 'cdbd6fdd-782a-4839-bb6c-5c60de12b550', url: 'https://github.com/Fatimezzahra-DARIM/day3-dev.git'
}
}
stage("Build") {
steps {
sh 'mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install'
}
}
stage("SonarQube Analysis") {
steps {
sh 'mvn sonar:sonar -Dsonar.host.url=$SONAR_URL'
}
}stage('Approve Deployment') {
input {
message "Do you want to proceed for deployment?"
}
steps {
sh 'echo "Deploying into Server"'
}
}
}


}