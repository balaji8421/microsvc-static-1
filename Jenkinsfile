pipeline {
    agent any
    environment {
        PATH= "${PATH}:/home/balaji/gradle-7.3.3/bin"
    }
    parameters{
        string(description: 'Type branch name to build', name: 'branch')
    }
    stages {
        stage('Clone Git Repo') {
            steps {
               echo "${params.branch}"
               git url: 'https://github.com/balaji8421/microsvc-static-1.git',branch:"${params.branch}"
            }
        }
        stage('Gradle Build') {
            steps {
               sh 'gradle clean build'
            }
        }
        stage('Ansible Deploy') {
            steps {
                ansiblePlaybook installation: 'Ansible', inventory: 'first_project/inventories/dev/hosts', playbook: 'first_project/ansible.yml'
            }
        }
    } 
}
