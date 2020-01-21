pipeline{
     agent any

     stages{
         stage("Buildstarted"){
            steps{
                slackSend channel: '#jenkins_build',
                    color: 'good',
                    message: "* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL} is started"
            }
        }
         stage('cleanWorkspace'){
            steps{
                step([$class: 'WsCleanup'])
}
}
         stage('clone'){
             steps{
                checkout ([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/Aliabbask08/testct.git']]])
}
}
         stage('BuildWithGradle'){
              steps{
                 echo "hello"
                 sh "pwd"
                 sh "gradle -v"
                 sh "gradle clean build"
}
}
         stage("BuildCompleted"){
            steps{
                slackSend channel: '#jenkins_build',
                    color: 'bad',
                    message: "* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL} is Completed"
            }
        }

}
}
