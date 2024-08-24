pipeline{
    agent none
    stages{
        stage('SCM'){
            steps{
                git url: 'https://github.com/dummyrepos-org/spring-petclinic.git',
                branch: 'main'
            }
        }
        stage('Build'){
            agent{
                label 'build'
            }
            steps{
                sh 'mvn clean package'
            }
        }
        stage('deploy'){
            parallel{
                stage('ST'){
                    agent{
                        label 'ST'
                    }
                    steps{
                        sleep(time: 5, unit: 'SECONDS')
                    }
                }
                stage('PT'){
                    agent{
                        label 'PT'
                    }
                    steps{
                        sleep(time: 5, unit: 'SECONDS')
                    }
                }

            }
        }
    }
}