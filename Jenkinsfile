node {
  def project = 'dev-mapping'
  def appName = 'dev'
  def imageTag = "gcr.io/${project}/${appName}:${env.BRANCH_NAME}.${env.BUILD_NUMBER}"

  checkout scm
  
  stage 'Current directory'
  sh("pwd")
  sh("mvn clean install")
  
  stage 'Build image'
  sh("docker build -t ${imageTag} .")
  
  stage 'Push image to registry'
  sh("gcloud docker -- push ${imageTag}")
  
}
