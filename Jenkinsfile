node("linux")
{
  stage("Unit Test")
  {
    git credentialsId: '11200248-9454-41a9-be09-1ae99a9bf5af', url: 'https://github.com/unnativoraUST/java-project.git'
    sh "ant -f test.xml -v"
    junit 'reports/result.xml'
  }
  stage("Build")
  {
    sh "ant -f build.xml -v"
  }
  stage("Deoploy")
  {
    sh "aws s3 cp /workspace/java-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://unnati-final"
  }
  stage("Report")
  {
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '0fda6a5e-0575-4e25-b0f5-de198d8150dd', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    sh "aws cloudformation describe-stack-resources --region us-east-1 --stack-name Jenkins"
  }
    
  }
}
