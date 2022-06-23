pipeline {
    agent any

    stages {
        stage('Compare checksum') {
            steps {
                script {
                    try {
                        check1=sh(returnStdout: true, script: 'shasum -a 512 check.txt')
                        println check1
                        // sh """
                        // #!/bin/sh
                        // check1=`shasum -a 512 check.txt`
                        // check2=`shasum -a 512 check2.txt` 
                        // echo $check1
                        // echo $check2
                        // """
                    } catch (err) {
                        println err
                        ERRORMESSAGE = "The hash codes doesn't match."
                        error "The hash codes doesn't match."
                    }
                }
            }
        }
    }
}
