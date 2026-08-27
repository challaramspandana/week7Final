pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo 'Build Docker Image'
                bat "docker build -t mypythonflaskapp ."
            }
        }
        stage('Run'){
            steps{
                echo 'Run application in Docker Container'
                bat "docker rm -f mycontainer || exit 0"
                //forcibly removes the Docker container names mycontainer
                //If the container does not exist, this command will fail and return an error
                //If failes execute exit 0 to ignore the error and continue with the next command
                bat "docker run -d -p 5000:5000 --name mycontainer mypythonflaskapp"
            }
        }
    }
    post{
        success{
            echo 'Pipeline completed successfully!'
        }
        failure{
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}