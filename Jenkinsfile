pipeline {

agent any
     
    stages {
        
     stage('Maven version') {
            steps {
                echo "Hello, Maven"
                sh "mvn --version" 
            }
        }
      
      
      
      stage('SonarCloud') {
  environment {
    SCANNER_HOME = tool 'Sonar'
    ORGANIZATION = "demo1_maven_freestyle"
    PROJECT_NAME = "demo1_maven_freestyle"
  }
  steps {
    withSonarQubeEnv('Sonarqube') {
        sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$ORGANIZATION \
        -Dsonar.java.binaries=build/classes/java/ \
        -Dsonar.projectKey=$PROJECT_NAME \
        -Dsonar.sources=.'''
    }
  }
}
      
      stage("Quality Gate") {
        steps {
        
           
              waitForQualityGate abortPipeline: true
     
        }
      }
        
        stage('Stage 1') {
            steps {
                sh 'mvn clean package'
            }
            
        }
        
        stage('Stage 2') {
            steps {
                echo 'Stage2 Hello world!'  
                echo  'Stage2 $date'
            }
            
        }
        
        
        stage('Stage 3') {
            steps {
                echo 'Wel come to Stage3 '  
                echo  'Stage3 '
            }
            
        }           
    }
}
