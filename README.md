# capstone-aws

project workflow:

The first thing I did was to download the code and move it to a new GitHub repository. Then I followed the instructions to set it up in a Docker container and pushed the Dockerfile to the repository. I spent some time navigating the website and reading the HTML code before fixing some issues and adding a News page, then I pushed the edited pages to the repository. The next step was to set up an EC2 instance and replicate the docker container there. After confirming that it functioned properly, I reviewed the provided CloudFormation template and made some slight changes and formatting fixes, namely allowing TCP traffic on port 22 for SSH traffic in the SecurityGroupIngress portion of the template. After using the template to launch the instance, I used PuTTy to connect with SSH and run the git clone and docker commands. I ran into a slight issue with permissions, so these commands were ran as the root user.

setup instructions:

run the cloudformation template
download the labuser.ppk (or pem on mac)
connect to the ec2 instance with ssh on port 22

run these commands:
	git clone "https://github.com/SS20x3/AWS-capstone-2.git"
	cd ./AWS-capstone-2
	docker build -t html-server-image:v1 .
	docker run -d -p 80:80 html-server-image:v1

there's a line in the cloud formation template that should allow the ec2@user to run docker commands, but if it doesnt work and the user doesn't have permissions, then do the commands as the root user with the 'sudo -i' command

key findings:

learned more about using docker and important commands to remember
learned more about using git with github from the windows termial
learned more about how to properly set up AWS CloudFormation templates