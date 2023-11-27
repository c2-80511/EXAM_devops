pipeline{
  agent any
  stages{
   stage('fetch from repo'){
    steps{
      sh 'git branch: 'master', url: 'https://github.com/c2-80511/EXAM_devops.git''
     }
   }

   stage('build image'){
     steps{
      sh '/usr/bin/docker image build -t prasadthombare/lab_exam .
     }
   } 
   
   stage('docker login'){
     steps{
       
       sh 'echo dckr_pat_CHPu1ilNJ-p1MFZJucnCfF_nOEA | /usr/bin/docker login -u prasadthombare --password-stdin'
       }
     }

    stage('push image'){
          steps{
          sh '/usr/bin/docker push image prasadthombare/lab_exam'
            }   

          } 

    stage('remove service'){
      steps{
      sh' /usr/bin/docker service rm mysvc'
         }
      }
    stage('start service'){
        steps{ 
       
         sh '/usr/bin/docker service create --name mysvc --replicas 5 -p 9876:80 prasadthombare/lab_exam
           }


       }
  
 }
}
