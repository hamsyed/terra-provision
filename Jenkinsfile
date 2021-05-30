pipeline{
    agent any
     environment {
      PATH = "${PATH}:${getterraform()}"
    }
    parameters {
    choice choices: ['Dev', 'Prod'], description: 'Please select the environment ', name: 'ENV'
   }
    
    stages {
        stage('terraform init and apply- ${params.ENV}'){
            steps {
               sh returnStatus: true, script: 'terraform workspace new ${params.ENV}'
                sh 'terraform init'
                sh 'terraform apply --auto-approve'
             }
           }
        }
}

def getterraform(){
  def terraform = tool name: 'Myterraform', type: 'terraform'
  return terraform
}
