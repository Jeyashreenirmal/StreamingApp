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

step 10 --- make ready the deployment and service yaml files for the application to deploy in EKS cluster. 

step 11  --- create an EKS cluster in AWS 

![eks cluster creation](screenshots/eks_cluster.png)

step 12 --- deployed the namespace yaml file 

![namespace](screenshots/namespace.png)

step 13 --- installed nginx ingress controller 

![ ingress controller instalation ](screenshots/ingress_controller.png)

step 14 --- apply secret yaml file 

![ secret yaml ](screenshots/secret.png)

step 15 --- deploy auth deployment and service yaml file 

![ authservice ](screenshots/authservice.png)

step 16 --- apply streaming deployment and service yaml file

![ streamingservice ](screenshots/streamingservice.png)

step 17 --- apply admin deployment and serivce yaml file

![ adminservice ](screenshots/adminservice.png)

step 18 --- apply chat deployment and service yaml file 

![ chatservice ](screenshots/chat.png)

step 19 --- apply frontend deployment and service yaml file

![ frontend service ](screenshots/frontend.png)

step 20 --- apply ingress yaml file 

step 21 --- output of web 

![ frontend web  ](screenshots/web1.png)

![ web  ](screenshots/web2.png)

![ web  ](screenshots/web3.png)

![ web  ](screenshots/web4.png)


step 22 --- installed cloudwatch obervability addon, followed by cloudwatch agent to track the metrics and fluent-bit to track the los 

![ cloudwatch pods](screenshots/cloudwatch_poods.png)

step 23 --- metrics output

![ metrics ](screenshots/container_insights1.png)
![ metrics ](screenshots/container_insights2.png)
![ metrics ](screenshots/container_insights3.png)
![ metrics ](screenshots/container_insights4.png)
![ metrics ](screenshots/container_insights5.png)

step 24 --- loggs 

![ loggs ](screenshots/loggs_1.png)

![ loggs ](screenshots/loggs_2.png)

![ loggs ](screenshots/loggs_3.png)

step 25 --- chatops, alarm creation and send notification through SNS (email)

![ alarm ](screenshots/alarm1.png)

![ alarm ](screenshots/alarm2.png)

![ alarm ](screenshots/alarm3.png)

step 26 --- SNS (email) notification 

![ SNS subcription confirmation ](screenshots/SNS_sub.png)

![ SNS alert ](screenshots/SNS_alert.png)

