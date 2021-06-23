pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {              
                checkout([$class: 'GitSCM', branches: [[name: '*/main/']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/adarshss27/jenkins_ansible_test.git']]])               
            } 
        }
        stage('build'){
            steps { 
            sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible', transfers: [sshTransfer(cleanRemote: false, excludes: '',execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: 'project_test2', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '*')]
            }
        }
        stage('Deploy'){
            steps {
                 shell 'ansible-playbook  /home/adarsh/project_test2/dir1/gather_fact.yml'
                 shell 'ansible-playbook  /home/adarsh/project_test2/dir2/gather_fact.yml'
            }
        }
                                                       
    }
}
