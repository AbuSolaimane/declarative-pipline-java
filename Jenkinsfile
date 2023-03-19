pipeline {
    agent any
    stages {
        stage('One') {
            steps {
                echo 'Hi this the first satge'
            }
        }
        stage('Two') {
            steps {
                input('do you want proceed?')
            }
        }
        stage('Three') {
            when {
                not {
                    branch "master";
                }
            }
            steps {
                echo 'stage three'
            }
        }
        stage('fourhree') {
            parallel {
                stage('unit test') {
                    steps {
                        echo 'unit test'
                    }
                }
                stage('integration test') {
                    agent {
                        docker {
                            reuseNode false
                            image 'ubuntu'
                        }
                    }
                    steps {
                        echo 'integration test'
                    }
                }
            }
        }
    }
}