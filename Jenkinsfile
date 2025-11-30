pipeline{
    agent any
    stages{
        stage(checkout){
            steps{
                checkout scm
            }
        }
        stage(build){
            steps{
                bat """
                mkdir out
                javac -d out src\\hello\\HelloWorld.java
                """
            }
        }
        stage(Run){
            steps{
                bat """
                java -cp out hello.HelloWorld
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
