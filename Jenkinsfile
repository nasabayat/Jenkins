pipeline {
    agent {
        docker { image 'golang:1.9.2-stretch'}
    }

    stages {
        stage('Build'){
            steps{
                sh 'go get -u github.com/jstemmer/go-junit-report'
                sh 'go build .'
            }
        }
        stage('Test'){
            steps{
                sh 'go test -v 2>&1 | go-junit-report > report.xml'
            }
        }
        stage('Deploy'){
            steps{
                echo "Tiny bubbles\nIn my beer\nMakes me happy\nAnd full of cheer"
            }
        }
    }
    // Required to view our test results in the UI
    post {
        always {
            junit 'report.xml'
        }
    }
}
