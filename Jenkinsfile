pipeline {
    agent any
    environment {
    PATH = "/usr/local/src/apache-maven/bin:$PATH"
    }
    stages {
        stage('GitHub Clone') {
            steps {
                git branch: 'project02', url: 'https://github.com/Chey2266/project-03-j2e.git'
            }
        }
        stage('Build Maven') {
            steps {
                sh "mvn clean install package"
            }
        }
        stage('Deploy Tomcat') {
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '3fe07e03-12fd-4199-8d53-2929a9dbfaf2', 
                path: '', 
                url: 'http://13.204.76.249:8080/')],
                contextPath: 'project-03-j2e', 
                war: '**/*.war'
            }
        }
        stage('add files') {
            git add Jenkinsfile 
            git add project-03-j2e
            git commit -m "initial commit"
            git remote add origin https://github.com/Chey2266/project-03-j2e.git
            git push -u origin project02
        }
    }
}

pipeline {
    agent any
    environment {
    PATH = "/usr/local/src/apache-maven/bin:$PATH"
    }
    stages {
        stage('GitHub Clone') {
            steps {
                git branch: 'project02', url: 'https://github.com/Chey2266/project-03-j2e.git'
            }
        }
        stage('Build Maven') {
            steps {
                sh "mvn clean install package"
            }
        }
        stage('Deploy Tomcat') {
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '3fe07e03-12fd-4199-8d53-2929a9dbfaf2', 
                path: '', 
                url: 'http://13.204.76.249:8080/')],
                contextPath: 'project02', 
                war: '**/*.war'
            }
        }
    }
}
