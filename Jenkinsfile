def server = Artifactory.server 'Artifactory server'
node {
   stage 'Checkout'
   git url: 'https://github.com/spring-projects/spring-petclinic.git'
   def mvnHome = tool 'mvn'
   
   try {
    stage 'Build'
    sh "${mvnHome}/bin/mvn clean install"
   
    stage 'Archive'
    archiveArtifacts 'target/petclinic.war'
   } catch (err) {
    emailext body: 'Hi, your build successfully failed', subject: 'Test jenkins', to: 's.g.ytsma@uu.nl'
   }
}
