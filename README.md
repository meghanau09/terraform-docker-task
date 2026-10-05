# Terraform Docker Container Provisioning

## Objective
Provision a Docker container using Terraform.

## Tools Used
- Terraform
- Docker

## Implementation

Terraform Docker provider was configured to create:
- nginx Docker image
- nginx container
- Port mapping 8081:80

## Terraform Commands Used

terraform init

terraform plan

terraform apply

terraform state list

terraform destroy

## Result

Successfully provisioned nginx container using Terraform.

## Below are the logs that I worked on.

# Terraform init

PS C:\ProjectsEL\terraform-docker-task> terraform init

Initializing the backend...

Initializing provider plugins...
- Finding kreuzwerker/docker versions matching "~> 3.0"...
- Installing kreuzwerker/docker v3.9.0...
- Installed kreuzwerker/docker v3.9.0

Terraform has been successfully initialized!

#Terraform Plan

PS C:\ProjectsEL\terraform-docker-task> terraform plan

Terraform will perform the following actions:

  # docker_container.nginx_container will be created
  # docker_image.nginx will be created

Plan: 2 to add, 0 to change, 0 to destroy.

# Terraform plan 

PS C:\ProjectsEL\terraform-docker-task> terraform apply

Do you want to perform these actions?
  Only 'yes' will be accepted to approve.

Enter a value: yes

docker_image.nginx: Creating...
docker_image.nginx: Creation complete

docker_container.nginx_container: Creating...
docker_container.nginx_container: Creation complete

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.

# Verify Docker container 

PS C:\ProjectsEL\terraform-docker-task> docker ps

CONTAINER ID   IMAGE          PORTS                    NAMES
25f1c9bc45b6   nginx:latest   0.0.0.0:8081->80/tcp     terraform-nginx

# Check terraform state

PS C:\ProjectsEL\terraform-docker-task> terraform state list

docker_container.nginx_container
docker_image.nginx

# Terraform Destroy

PS C:\ProjectsEL\terraform-docker-task> terraform destroy

Plan: 0 to add, 0 to change, 2 to destroy.

Do you really want to destroy all resources?

Enter a value: yes

Destroy complete! Resources: 2 destroyed.

# Troubleshooting port since 8080 was already in use so I've used 8081

Error: Unable to start container
ports are not available: 8080