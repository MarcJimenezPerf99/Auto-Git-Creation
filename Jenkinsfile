pipeline {
    agent any
    parameters {
        string(name: 'repoName', defaultValue: '', description: 'The desired name for the repository')
    }
    stages {
        stage('Create Git Repo') {
            steps {
                echo 'Access API and make repo'
                withCredentials([usernamePassword(credentialsId: 'b88bbcb5-59bf-4bb3-a8e5-9f3c4d080639', passwordVariable: 'pass', usernameVariable: 'user')]) {
                    sh 'curl -X POST -i -H \"Authorization: token $pass\" --data "{\\"name\\":\\"$repoName\\"}" https://api.github.com/user/repos'
                }
                // Local Jenkins Credentials below
                // withCredentials([usernamePassword(credentialsId: '0baa423f-35a5-44ca-b95d-c742463e9afa', passwordVariable: 'pass', usernameVariable: 'user')]) {
                //  sh 'curl -X POST -i -H "Authorization: token $pass" --data "{\\"name\\":\\"test_repo\\"}" https://api.github.com/user/repos'
                // }
            }
        }
    }
    post {
        success {
            echo "Successfully made new repo"
            cleanWs()
        }
    }
}