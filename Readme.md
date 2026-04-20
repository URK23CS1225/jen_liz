docker rm jenkins

docker run -d --name jenkins -u root -p 8080:8080 -p 50000:50000 -v jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock jenkins/jenkins:lts

docker exec -u 0 -it jenkins bash

apt update

apt install -y docker.io

usermod -aG docker jenkins

exit

docker restart jenkins

docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword

open : localhost:8080