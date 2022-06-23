pipeline {
    agent any

    stages {
        stage('Compare checksum') {
            steps {
                script {
                    try {
                        check1=sh(returnStdout: true, script: 'md5sum check.txt').replace(' check.txt', '')
                        check2=sh(returnStdout: true, script: 'md5sum check2.txt').replace(' check2.txt', '')
                        println check1
                        println check2
                        if (check1.equals(check2)) {
                            println "They are the same"
                        }
                        else {
                            throw new Exception('Error')
                        }
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
