pipeline {
    agent any
    stages {
        stage( 'Build' ) {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        stage ( 'Build docker image' ) {
            when {
                branch 'master'
                 }
            steps {
                script {
                    app = docker.build(charanthakur/trainschedule)
                    app.inside {
                        sh 'echo $(curl localhost:8080)'
                                }
                        }
                  }
        }
        
                
            
        
    }
}
