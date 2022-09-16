pipeline {
  environment {
    registry = "http://52.66.207.155:8083/repository/docker-grp/"
    registryCredential = 'nexusrepo'
    }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git branch: 'main', url: 'https://github.com/pmoghle/sonar.git'
      }
    }
   stage('Building image') {
      steps{
        script {
          sh 'docker build -t flask -f ./Dockerfile.txt .' 

        }
       }
	  }
    stage('Deploy Image in to nexus registry') {
      steps{
        script {
	  sh 'sudo docker tag flask 2.66.207.155:8083/repository/docker-grp/flask'
	  sh 'sudo docker login -u admin -p pooja 52.66.207.155:8083/repository/docker-grp/' 
          sh 'sudo docker push 2.66.207.155:8083/repository/docker-grp/flask'
          sh 'sudo docker logout 2.66.207.155:8083/repository/docker-grp/'
          // sh 'curl -XGET "admin:pooja" -X PUT http://3.110.86.199:8081/repository/python/flask-app '
	    }
          }
        }
      }
    }
//  stage('scan and build Jar file') {
// 	  script {
// 	       withSonarQubeEnv('SonarQube Scanner')
//         //   sh 'mvn clean package sonar:sonar' 
// 	     //sh "${scannerHome}/bin/sonar-scanner"
// 		sh "${scannerHome}/bin/sonar-scanner"


// 	      }
//             }
//stage('SonarQube analysis') {
//         script {
//           // requires SonarQube Scanner 2.8+
//         //  scannerHome = tool 'SonarQube Scanner 2.8'
//         }
// 	// node('SonarQube Scanner')
//         withSonarQubeEnv('SonarQube Scanner') {
//           sh "${scannerHome}/bin/sonar-scanner"
//         }
//       }
    
          
          

        
