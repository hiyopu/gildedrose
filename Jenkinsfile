node {
stage('Preparation') {
      git 'https://github.com/meekrosoft/gildedrose.git'
   }
   
   stage('Build') {
        sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn install'
   }
   
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
      
   stage('Javadock') {
      sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'
      archive 'target/javadock'
      archive 'target/gildedrose-*.jar'
   }
}
