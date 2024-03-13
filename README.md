# Running Ansible Playbook with Docker

This repository contains an Ansible playbook for deploying a Docker container with a React app using Apache. Below are instructions on how to run the Ansible playbook using Docker and what to expect as output.

## Prerequisites

Make sure you have the following installed on your system:

- Docker
- Ansible

## How to Run

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/your-username/your-repository.git
Navigate to the repository directory:

   bash
   cd your-repository
Run the Ansible playbook using Docker:

    bash
docker run --rm -v $(pwd):/ansible -w /ansible williamyeh/ansible:alpine3 ansible-playbook playbook.yml
This command mounts the current directory ($(pwd)) as a volume inside the Docker container and sets it as the working directory. Then, it executes the ansible-playbook command within the container.

## Expected Output
The playbook will install the Docker Python module, create a Docker network, and deploy a Docker container with Apache serving a Html Page.
The IP address of the container will be retrieved and stored in ip.txt.
You can find the IP address of the container in the ip.txt file.
The React app build files will be copied to the host machine's /tmp/network directory.
Additionally, the IP address of the container will be displayed as output.
Viewing the Html Page
Once the playbook execution is complete, you can access the Html Page served by Apache using the IP address of the Docker container. Open a web browser and navigate to http://<container-ip>. Replace <container-ip> with the IP address retrieved from the ip.txt file.

## Cleaning Up
After you're done testing, you can remove the Docker container and network by running:

 ```bash
docker container stop $(docker container ls -aq) && docker network prune -f