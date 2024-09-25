pipeline{
    agent any
    stages{
    stage('ContiDown'){
        steps
        {
            git 'https://github.com/intelliqittrainings/maven.git'
        }
    }
        stage('ContiBuild')
        {
            steps{
            sh 'mvn package'
        }
        }
        stage('ContDeploy'){
            steps{
            deploy adapters: [tomcat9(credentialsId: '15231163-e7af-4e77-84f0-510d6a5742e7', path: '', url: 'http://172.31.38.18:8080')], contextPath: 'test', war: '**/*.war'
        }
}
        stage('ContTest'){
            steps{
            git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
            sh 'java -jar /var/lib/jenkins/workspace/declarative1/testing.jar'
        }
        }
        stage('ContDel'){
            steps{
            deploy adapters: [tomcat9(credentialsId: '15231163-e7af-4e77-84f0-510d6a5742e7', path: '', url: 'http://172.31.47.172:8080')], contextPath: 'prod', war: '**/*.war'
            }
        }
    
}
}
