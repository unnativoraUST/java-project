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
}
