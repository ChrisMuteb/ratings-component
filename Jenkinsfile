pipeline{
    agent any

    environment {
        AWS_DEFAULT_REGION = 'eu-west-1'
        S3_BUCKET = 'ratings-component'
    }
    parameters {
        booleanParam(
            defaultValue: false,
            description: 'Sync with s3 bucket',
            name: 'MY_SYNC_PARAM'
        )
    }

    stages {
        stage('Build'){
            steps {
                echo 'hello ratings component'
            }
        }
        stage('Test'){
            steps{
                echo 'build: ratings-component'
            }
        }
        stage('Deploy'){
            when{
                expression {
                    params.MY_SYNC_PARAM
                }
            }
            steps{
                echo 'Deploy: ratings-component'
                // sh 'aws s3 sync . s3://$S3_BUCKET --delete --exclude ".git/*"'
            }
            
        }
    }
}