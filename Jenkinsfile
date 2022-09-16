pipline{
  agent none
  stages{
    stage('Build'){
      agent{
        docker{
          image 'python:2-alpha'
        }
      }
    stage{
      sh 'python -m py_compile sources/add2vals.py sources/calc.py'
      }
    }
    stage('Test'){
      agent{
        docker{ 
          image 'qnib/pytest'
        }
      }
      steps{
        sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_calc.py'
      }
      post{
        alway {
          junit 'test-reports/results.xml'
        }
      }
    }
  } 
}









