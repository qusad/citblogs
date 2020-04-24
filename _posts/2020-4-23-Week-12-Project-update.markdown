---
layout: "post"
---
I am slowly progressing with the file upload part but I have ran into a few hiccups. First, the EC2 assume role from the previous blog is not working in a way that I would like it to. Apparently the assume role feature grants the EC2 instance the access to various AWS resources, but this does not apply to application within the EC2. For example, I can run the 'aws s3 ls' command to list all buckets associated with my account without proving any credentials or setting up the AWS-CLI module. AWS provides documentation for almost all SDK and programming languages except PHP for this specific modules. I will try to play around with the permissions to see if there is anything I can do.

The next part is still in progress but seems to work so far. I am using the AWS PHP SDK to upload files from the local server to the S3 bucket. The file is first uploaded to the local server and then uploaded to the S3 bucket. I am using the user's username in the upload code to create a unique folder for each user. I am looking into more secure ways to upload and store file, such as encrypting the folder name, encrypting the file in transit and rest, as well as checking the file before it is sent to the S3 bucket.

<img src='https://raw.githubusercontent.com/qusad/citblogs/gh-pages/Capture2.PNG'>

My next goal is to list all files in the user's folder and create download links for all. 
