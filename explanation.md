## Choice of the base image on which to build each container

> Alpine are smaller in size, that consume less disk space

## Dockerfile Directives

> The database service doesn't require additional directives since we're using an official image.
> The Dockerfile for the client service doesn't need custom directives either.
> In the Dockerfile for the backend service, we use WORKDIR to set the working directory, COPY to copy the application code, and RUN to install Node.js dependencies with npm install.

## Docker-compose Networking

> I used a default bridge network for our Docker Compose setup, which allows containers to communicate with each other using their service names as hostnames.

## Docker-compose Volume definition and usage

> For the client and backend services, I did not need volumes since they serve static files or run stateless applications.

## Git Workflow

> To not corrupt the main branch,one creates a new branch or features or bug fixes, and we merge these branches into the main branch when ready.
> Git workflow allows us keep track with the feature versioning.

## Successful Running and Debugging

> I trace the bugs and their solution with git commits. 
> To ensure successful running, I regularly test my Docker Compose setup on local environments before deploying it to production.
> The major bug was running the package.json to pick a lower version of the node module, to resolve this I created a new image and adjusted the dockerfile to run the package.json adding commands like;

> ```COPY package*.json ./```

> ```RUN npm ci```

> ```RUN npm install -g npm@16.0.0```

## Docker Image Tag Naming

> I have used the naming convention to be first, ip-clientv1.0.0 but on the final image it reads frontend-ip2v1.0.1 - this convention is because it is a bug tagging that is why I have not written it as v2.0.0

## Set up the environment by provisioning a vagrant virtual machine 

> The vagrant virtual machine that is used in the project is geerlingguy/ubuntu2004.
> I have used vagrant to provision the ansible playbooks, which in turn, install docker, clone the project from github.
> The command to run the vagrant is ```vagrant up ```

## Ansible Roles

> Since ansible roles are re-usable, I have implemented them in gitinstall and install docker.
> Within the git install folder, I have created tasks for cloning the git project.
> For the installdocker folder, I have created tasks for installation and written the variables in the vars folder.

## Ansible Playbook

> To automate the process, I have the playbook.yml, that runs the above roles.
> Since roles are sudo processed, the commands in the playbooks access the permissions to the roles folder.

## Test-Run
> To run the application; ```docker compose up```
> Run ```docker ps -a``` to verify the running cntainers
> 
> Run ```vagrant provision``` to execute the playbook and run the vm
> ```vagrant ssh ```into the vagrant