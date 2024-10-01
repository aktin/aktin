pipeline {
    agent any
    
    tools {
        maven 'Default'
    }

    stages {
        stage('Checkout Submodules') {
            steps {
              sh 'git submodule update --init'
            }
        }
        
        stage('Build') {
            steps {
                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    sh 'mvn clean install -DskipTests=true'
                }

                withEnv(["JAVA_HOME=${ tool 'Java8' }"]) {
                    dir('dwh-api') {
                        sh 'mvn clean install -DskipTests=true'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    dir('r-script') {
                        sh 'mvn clean install -DskipTests=true'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    dir('dwh-db') {
                        sh 'mvn clean install -DskipTests=true'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java8' }"]) {
                    dir('dwh-import') {
                        sh 'mvn clean install -DskipTests=true'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java8' }"]) {
                    dir('dwh-prefs') {
                        sh 'mvn clean install -DskipTests=true'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java8' }"]) {
                    dir('dwh-query') {
                        sh 'mvn clean install -DskipTests=true'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    dir('dwh-admin') {
                        sh 'mvn clean install -DskipTests=true'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    dir('dwh-j2ee') {
                        sh 'mvn clean install -DskipTests=true'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    sh 'mvn test'
                }

                withEnv(["JAVA_HOME=${ tool 'Java8' }"]) {
                    dir('dwh-api') {
                        sh 'mvn test'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    dir('r-script') {
                        sh 'mvn test'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    dir('dwh-db') {
                        sh 'mvn test'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java8' }"]) {
                    dir('dwh-import') {
                        sh 'mvn test'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java8' }"]) {
                    dir('dwh-prefs') {
                        sh 'mvn test'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java8' }"]) {
                    dir('dwh-query') {
                        sh 'mvn test'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    dir('dwh-admin') {
                        sh 'mvn test'
                    }
                }

                withEnv(["JAVA_HOME=${ tool 'Java11' }"]) {
                    dir('dwh-j2ee') {
                        sh 'mvn test'
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
