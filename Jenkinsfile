pipeline {
    agent any
    parameters {
        booleanParam(name: 'DESTROY_BEFORE', defaultValue: false, description: 'Destroy Infrastructure')
        booleanParam(name: 'DEPLOY_APP', defaultValue: true, description: 'Deploy Application')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run Tests')
        booleanParam(name: 'VULCAN_TAG', defaultValue: true, description: 'Tag Commit with Vulcan on Success')
        booleanParam(name: 'DESTROY_AFTER', defaultValue: true, description: 'Destroy Infrastructure')
        booleanParam(name: 'DEBUG', defaultValue: false, description: 'Show Verbose Output')
    }
 
    stages {
        stage('Deployment') {
            when {
                expression { params.DESTROY_BEFORE || params.DEPLOY_APP }
            }
            steps {
                echo 'Performing Deployment...'
                // Add deployment steps here
            }
        }
        stage('Test') {
            when {
                expression { params.RUN_TESTS }
            }
            steps {
                echo 'Running Tests...'
                // Add testing steps here
            }
        }
        stage('Tagging') {
            when {
                expression { params.VULCAN_TAG }
            }
            steps {
                echo 'Tagging Commit with Vulcan...'
                // Add tagging steps here
            }
        }
        stage('Cleanup') {
            when {
                expression { params.DESTROY_AFTER }
            }
            steps {
                echo 'Performing Cleanup...'
                // Add cleanup steps here
            }
        }
    }
    options {
        disableConcurrentBuilds()
    }
}
