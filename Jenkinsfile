pipeline {
	agent {
	 label {
	 lable ("built-in")
	 customWorkspace "/mnt/23Q1"
	 }
	}
		stages {
			stage ('Install Docker') {
				steps {
					sh 'yum install docker -y ; systemctl start docker'
			}
			}
			stage ('Clone Repository') {
				steps {
					checkout scm
				}
			}
			stage ('Deploy to 23Q1') {
			when {
				branch '23Q1'
			}
				steps {
					sh 'docker run -itdp 80:80 --name 23Q1 httpd'
					sh 'docker cp /mnt/23Q1/index.html 23Q1:/usr/local/apache2/htdocs'
				}

			}
		}
}
