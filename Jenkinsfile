pipeline {
  agent any

  environment {
    DIRECTORY_PATH = '/path/to/source/code'
    TESTING_ENVIRONMENT = 'staging'
    PRODUCTION_ENVIRONMENT = 'production'
  }

  stages {
    stage('Build') {
      steps {
        echo 'Fetching the source code from the directory path specified by the environment variable.'
        echo "Directory Path: $DIRECTORY_PATH"
        echo 'Compile the code and generate any necessary artifacts.'

        echo 'Maven can be used for building the code'
        echo "Example: sh 'mvn clean package'"
      }
    }

    stage('Test') {
      steps {
        echo 'Running unit tests.'
        echo 'Running integration tests.'
        echo 'Tools like JUnit for unit tests and Selenium for integration tests can be used'
      
      }
      post {
        success {
          mail subject: 'Build Success Notification',
                    body: 'The build completed successfully.',
                    to: 'bpillwein23@gmail.com'
        }
        failure {
          mail subject: 'Build Failure Notification',
                    body: 'The build failed.',
                    to: 'bpillwein23@gmail.com'
        }
      }
    }

    stage('Code Quality Check') {
      steps {
        echo 'Checking the quality of the code.'
        echo 'SonarQube can be used for code quality analysis'
      }
    }

    stage('Security Scan') {
      steps {
        echo 'Performing security scan on the code.'
        echo 'OWASP ZAP can be used for security scanning'
      }
      post {
        success {
          mail body: 'The security scan stage completed successfully.',
            subject: 'Security Scan Success',
            to: 'bpillwein23@gmail.com',
            // attachLog: true
        }
        failure {
          mail body: 'The security scan stage failed.',
            subject: 'Security Scan Failed',
            to: 'bpillwein23@gmail.com',
            // attachLog: true
        }
      }
    }

    stage('Deploy to Staging') {
      steps {
        echo 'Deploying the application to a testing environment specified by the environment variable.'
        echo 'Jenkins Pipeline AWS Steps or AWS CLI can be used for deployment to AWS EC2 instance'
      }
    }

    stage('Integration Tests on Staging') {
      steps {
        echo 'Running integration tests on the staging environment.'
        echo 'Similar tools used in the Test stage can be utilised for integration tests on staging'
      }
    }

    stage('Deploy to Production') {
      steps {
        echo 'Deploying to Production'
        echo "Deploying from $TESTING_ENVIRONMENT to $PRODUCTION_ENVIRONMENT"
        echo 'Similar deployment tools as used in Deploy to Staging stage can be used for production deployment'
      }
    }
  }
}