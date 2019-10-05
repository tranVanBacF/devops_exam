# devops_exam
Exam DevOps

Họ và tên: Lê Hải Trung
Account: TrungLH3
Đơn vị: FHN.ICE

# Dockerfile

FROM tomcat:jdk8-openjdk-slim
LABEL version="1.0"
ADD . /code
WORKDIR /code
RUN rm -rf /usr/local/tomcat/webapps/ROOT
COPY ROOT.war /usr/local/tomcat/webapps

# Network

docker network create -d bridge --subnet 10.10.20.0/24 devops-exam

# Build images

docker build -t devops_exam .

# Run container

docker run --network=devops-exam -d --name=devops_exam_server -p 8080:8080 devops_exam
