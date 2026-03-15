step 1 ----- fork the repo
step 2 --- create the docker file for each sevices. 
step 3 --- create an ECR repository in aws

![ecr repo](screenshots/ecr_repo.png)

step 4 --- Authenticate Docker to AWS ECR
![docker authetication](screenshots/docker_auth.png)

step 5 ---build the image

step 6 ---tag the image 

step 7 ---push the image into AWS ECR

![docker push](screenshots/docker_push.png)

step 8 --- do the same for the other services. 

![docker ecr of all services](screenshots/docker_ecr.png)

step 9 --- build the pipeline to automate the docker image deployment process

![jenkins ](screenshots/Jenkins.png)


