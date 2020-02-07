---
layout: "post"
---
The work has started and we are working out a plan of action. There are several main things that need to be done:
1. Setup the initial infrastructure. We wil be using a similar setup as the last project. 2-3 Web server EC2 instances, a bastion, Application Load Balancer and other necessary tools and services. 
2. Setup the AWS RDS database using MySQL engine. This will be done using Terrafrom and the respective modules. There is one problem with automating the process. AWS assignes a random enpoint name to the RDS instance which is needed inside the site files to access the database. A possible solution is to use Ansible rds_instance_info module to grab the endpoint after instance creation and use Ansible to edit the site files before they are uploaded to the web server.
3. We also need a mailing service for the user account confirmation and logging. Previously we used PHPMailer library to locally host the mailing server. This is not feasible with the proposed AWS infrastructure. We will look into AWS Simple Notification and Simple Email Services to accomplish this task.
4. We also want to look into other AWS services to get more pratice. I want to play around with CloudWatch and create a mobile/email notification for when a new user signs up for out application. We also thought of trying AWS AutoScaling and AMI packaging for up/downscaling our infrastructure. 

In the meantime I am going over the AWS training videos and slides to prepare for the certification. 
