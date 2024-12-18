pipeline {
    //commentforPOLSCM
    agent 
    {
        label 'slave3'
    }
tools 
{
    maven 'Maven-Slave'
}
    stages 
    {
        stage('git-pull') 
        {
            steps {
                echo 'Pulling Code from GIT'
                git credentialsId: 'git-1', url: 'https://github.com/leenadharmik/project.git'
            }
        }
    stage('build-rar')
    {
        steps
        {
        echo "Building rar file in slave"
        sh 'mvn clean install'
        }
    }
    stage('Deploy WAR')
    {
    steps
    {
        echo "DEploying WAR to Slave3 machine"
        sh 'sudo cp /mnt/jenkins-slave/workspace/cicd-script-pipeline-upload/target/LoginWebApp.war /mnt/servers/apache-tomcat-9.0.98/webapps'
    }
    }
    
    }
}

