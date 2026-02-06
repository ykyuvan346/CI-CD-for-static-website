pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                // Replace with your GitHub username and repo
                git branch: 'main', url: 'https://github.com/ykyuvan346/CI-CD-for-static-website.git'
            }
        }

        stage('Deploy to EC2') {
            steps {
                // Use the Jenkins SSH credential you created
                sshagent (credentials: ['ec2-key']) {
                    sh '''
                        # Copy all files to the EC2 website folder
                        scp -r * ubuntu@13.201.60.11:/var/www/html/website/

                        # Restart Apache to apply changes
                        ssh ubuntu@13.201.60.11 'sudo systemctl restart apache2'
                    '''
                }
            }
        }
    }
}
