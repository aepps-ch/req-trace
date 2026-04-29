# Autodeployment

Add a github ci-action which builds the docker-image and deploys it on ghci.io.  
Add this deploy-script as a submodule: https://gist.github.com/timble-one/0cf1d8ef20f45662cfc31f5e894e9a8d  and make sure the `make pull-prod` and `make prod` targets exist in this project.  
The last step of the github-workflow must be to deploy the project on the production server.   
For the production-deployment, the github-workflow must use apleboy/ssh-action and only pass `host` and `username` as github-variable and the `key` as github-secret to the ssh-action.  
The ssh-connection will automatically trigger the deployment-script on the production-server. The script does not have to be called explicitly from the github-workflow.  
