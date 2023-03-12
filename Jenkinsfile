pipeline{
    agent {label 'agent'}
    trigers{ pollSCM('* * * * *') }
    stages{
        stage('vcs'){
            steps{
                git url: 'https://github.com/spring-projects/spring-petclinic.git',
                    branch: 'main'
            }
        }
        stage('maven_build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('ansible'){
            steps{
                sh 'ansible-playbook -i hosts spc.yml'
            }
        }
    }
}