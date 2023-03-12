pipeline{
    agent {label 'agent'}
    triggers{ pollSCM('* * * * *') }
    tools{
        maven 'maven'
    }
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
        stage('copy'){
            steps{
                sh 'cp /home/sai/workspace/petclinic/target/*.jar /home/sai/'
                sh 'cp /home/sai/spc.yml /home/sai/workspace/petclinic/'
            }
        }
        
        stage('ansible'){
            steps{
                sh 'ansible-playbook -i hosts /home/sai/workspace/petclinic/spc.yml'
            }
        }
    }
}
