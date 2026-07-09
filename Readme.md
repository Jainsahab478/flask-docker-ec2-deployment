#Flask Docker EC2 Deployment

A simple Flask web app, containerized with Docker and deployed on an AWS EC2 instance. Built this to actually learn how deployment works end to end instead of just reading about it.

#What it does

Basic Flask app with a home page and an about page. Nothing fancy on the app side — the point of this project was the deployment part, not the app itself.

#Stack


Flask (Python)
Docker
AWS EC2 (Ubuntu, t2.micro - free tier)


#How it's deployed


Built a Dockerfile for the Flask app
Tested it locally with docker build and docker run
Launched an EC2 instance (Ubuntu, free tier)
Configured the security group to allow inbound traffic on port 9000
Copied the project files to the instance using scp
Installed Docker on the instance
Built and ran the container on EC2
Verified it was reachable from a browser using the instance's public IP


#Running it locally

bashgit clone https://github.com/Jainsahab478/flask-docker-ec2-deployment.git
cd flask-docker-ec2-deployment
docker build -t tryout-app .
docker run -p 9000:9000 tryout-app

Then open http://localhost:9000

Notes / things I ran into



Spent a while debugging why port 9000 wasn't reachable even with the security group configured correctly. Checked Docker's port mapping, the security group attachment, and ufw status before finding the actual issue.
The instance is stopped when not in use to stay within free tier limits, so the IP in any screenshots here won't be live.


What's next

Planning to add a GitHub Actions workflow so pushes to main auto-build and redeploy to EC2, instead of doing it manually with scp and docker build every time.

About me

CS undergrad learning DevOps by building and deploying real (if small) projects. More at GitHub and DockerHub.