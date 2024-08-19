pipeline
{
    agent
    {
        node 
        {
            label 'JenkinsSlaveNodeLabel'
        }
    }
    stages
    {
        stege("Checkout code")
        {
            steps
            {
                git url : 'https://github.com/devopsak1/jenkins_repo_2_ci_cd.git',branch:'main'

            }
        }
        steage("Clean Up stage")
        {
            steps
            {
                sh 'docker rm -f $(docker ps -aq)'
                sh 'docker rmi -f myimage'
            }
        }
        stage("Bulid Image stage ")
        {
            steps
            {
                sh 'docker build -t myimage .'
            }
        }
        stage("Push image to Dockerhub stage")
        {
            steps
            {
                sh 'docker tag myimage akdochub/dockerhubjenkinsrepocicd:V.1'
                sh 'docker run -d -p 8501:8501 myiamge'

            }
        }
        stage("Deploye Kubernetes")
        {
            steps
            {
                sh 'kubctl apply -f my-deployment.yml'
            }
        }
    }
}