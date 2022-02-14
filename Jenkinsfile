pipeline {
    agent any
    stages {
        // stage('SCM'){
        //     // steps {
        //     //     deleteDir()
        //     //     echo 'Get Jenkinsfile from repo'
        //     //     checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[]]])
        //     // }
        // /}
        stage('Create Git Repo') {
            steps {
                echo 'Access API and make repo'
                // withCredentials([sshUserPrivateKey(credentialsId: 'f12898cd-0a9b-42d7-9ade-f2afd583f009', keyFileVariable: '', passphraseVariable: 'pass', usernameVariable: 'user')]) {
                //     sh 'curl -u "MarcJimenezPerf99:\'{$pass}\'" https://api.github.com/user/repos -d \'{"name":"test"}\''
                // }
                withCredentials([usernamePassword(credentialsId: '0baa423f-35a5-44ca-b95d-c742463e9afa', passwordVariable: 'pass', usernameVariable: 'user')]) {
                    sh 'curl -X POST -i -H "Authorization: token $pass" --data \"{\"name\":\"test_repo\"}\" https://api.github.com/user/repos'
                }
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