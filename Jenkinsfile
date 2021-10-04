pipeline {
agent any
stages {
stage ('Compile Stage') {
steps {
withMaven(maven : 'apache-maven-3.6.1') {
bat'mvn clean compile'
}
}
}
stage ('Testing Stage') {
steps {
withMaven(maven : 'apache-maven-3.6.1') {
bat'mvn test'
}
}
}
stage ('Install Stage') {
steps {
withMaven(maven : 'apache-maven-3.6.1') {
bat'mvn install'
}
}
}
}
}
post {
    failure {
      // The developer setting up this job can specify which group should receive an email when the build fails
      mail to: "${emailRecipient}",
        subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
        body: "Something is wrong with ${env.BUILD_URL}"
    }
  }
}
