Building docker image and pushing to ECR
```
sudo docker build -t albertleng-ecr-repository-18032024:latest .
docker tag albertleng-ecr-repository-18032024:latest 255945442255.dkr.ecr.us-east-1.amazonaws.com/albertleng-ecr-repository-18032024:latest
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 255945442255.dkr.ecr.us-east-1.amazonaws.com
docker push 255945442255.dkr.ecr.us-east-1.amazonaws.com/albertleng-ecr-repository-18032024:latest
```

Pulling from ECR and running locally
```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 255945442255.dkr.ecr.us-east-1.amazonaws.com
docker pull 255945442255.dkr.ecr.us-east-1.amazonaws.com/albertleng-ecr-repository-18032024:latest
docker run -d -p 8080:80 --name my-web-server 255945442255.dkr.ecr.us-east-1.amazonaws.com/albertleng-ecr-repository-18032024:latest
```