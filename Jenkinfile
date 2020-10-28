pipeline{
  agent any  
  stages {
   stage("Opening"){
         steps{
            //Welcome message
            script{
               sh "echo 'Welcome to Jenkins'"
}
}
}

   stage("Workspace_cleanup"){
        //Cleaning WorkSpace
        steps{
            step([$class: 'WsCleanup'])
}
}

   stage("Repo_clone"){
       //Clone repo from GitHub
      steps {
         checkout ([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'instance_id', url: ''git@github.com:Vikas-Tamboli/calculator.git]]])

}
}

  stage("static analysis"){
       //static analysisi for javascript 
       steps {
          sh '''
             cd js
             jshint --verbose index.js
             cd -
          '''
}
}

  stage("build"){
       //build calculator
       steps {
         sh '''
            cp -r js/ /var/www/html/
            cp -r index.html /var/www/html/
            cp -r css/ /var/www/html/
         ''' 
   
}
}

} 
}
