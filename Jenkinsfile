pipeline {
    agent any

    stages {
        stage('Compare checksum') {
            steps {
                script {
                    try {
                        sh """
                        echo=`shasum -a 512 check.txt`
                        echo=`shasum -a 512 check2.txt` 
                        """
                        /*def stopPrimary = sh(returnStdout: true, script: "hello | md5sum").trim()
                        println stopPrimary
                        println "Comparing..."
                        sleep(10)*/
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
