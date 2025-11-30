pipeline{
    agent any
    stages{
        stage(checkout){
            steps{
                checkout scm
            }
        }
        stage('build'){
            steps{
                bat """
                mkdir out
                javac -d out src\\hello\\Hello.java
                """
            }
        }
        stage('Run'){
            steps{
                bat """
                java -cp out hello.Hello
                echp Build_OK >artifact.txt
                """
            }
        }
    }
    post{
        always{
            archiveArtifacts artifacts: 'artifact.txt', fingerprint: true
        }
    }
}
