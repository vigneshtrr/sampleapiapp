
pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Restore packages'){
           steps{
             
             bat "dotnet restore"
            }
         }
        stage('Clean'){
           steps{
               bat 'dotnet clean --configuration Release'
            }
         }
        stage('Build'){
           steps{
               bat 'dotnet build --configuration Release --no-restore'
            }
         }
        //stage('Test: Unit Test'){
          // steps {
            //    sh 'dotnet test XUnitTestProject/XUnitTestProject.csproj --configuration Release --no-restore'
            // }
        //  } 
        stage('Publish'){
             steps{
               bat 'dotnet publish samplecorewebapi.csproj --configuration Release --no-restore'
             }
        }
        stage('Deploy'){
             steps{
           //    sh '''for pid in $(lsof -t -i:9090); do
             //          kill -9 $pid
             //  done'''
                bat 'Xcopy "C:/ProgramData/Jenkins/.jenkins/workspace/multi_branch_master/bin/Release/netcoreapp3.1/publish/" "C:/inetpub/wwwroot/samplewebapi/publish/"'
               // sh 'nohup dotnet WebApplication.dll --urls="http://104.128.91.189:9090" --ip="104.128.91.189" --port=9090 --no-restore > /dev/null 2>&1 &'
             }
        }
    }
}
