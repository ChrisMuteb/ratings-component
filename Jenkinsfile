pipeline{
    agent any

    environment {
        AWS_DEFAULT_REGION = 'eu-west-1'
        S3_BUCKET = 'ratings-component-eu'
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
                withCredentials([
                    string(credentialsId: 'aws-access-key-id-lsp', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key-lsp', variable: 'AWS_SECRET_ACCESS_KEY')
                ]){
                    echo 'Deploy: ratings-component...'
                    sh '''
                        echo "Deploying to S3..."
                        aws s3 sync . s3://$S3_BUCKET \
                        --delete \
                        --exclude ".git/*" \
                        --exclude "Jenkinsfile" \
                        --exclude "*.md"
                    '''
                }
            }
            
        }
    }
}