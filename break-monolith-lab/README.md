# Break a Monolithic Application into Microservices 


## Pre-Lab
- Install and configure the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
- Install and configure [AWS Copilot](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Copilot.html#copilot-install)
- Install and configure [Docker](https://docs.docker.com/get-docker/)
- Install and configure git

## Lab Instructions

### Setup
1. Run `git clone https://github.com/awslabs/amazon-ecs-nodejs-microservices`.

### Containerize and Deploy the Monolith
1. Create a Copilot application by running the following script:
```bash
cd ./amazon-ecs-nodejs-microservices/
copilot app init
```
2. Run `copilot env init`. 
3. Name the environment `api`.
4. Choose `profile default`
5. Select `Yes, use default.`
6. Deploy the environment by running `copilot env deploy --name api`.
7. Create a copilot service by running `copilot svc init`.
8. Select `Load Balanced Web Service`.
9. Name the service `monolith`
10. Enter the path to `2-containerized/services/api/Dockerfile`
11. Deploy the copilot service by running `copilot svc deploy --name monolith`

You can try testing the app by visiting the url. eg. `http://<application-string>.us-east-1.elb.amazonaws.com/api/users/3`