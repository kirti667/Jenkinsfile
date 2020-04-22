pipeline { 
    agent {
        lable 'worker'
   
   stages {
        stage('Build') {
            steps {
                sh 'mvn package'
                }
        }
        stage('Test') {
            agent {
                lable 'master'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
