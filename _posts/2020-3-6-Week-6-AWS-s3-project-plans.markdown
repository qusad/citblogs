---
layout: "post"
---
After the initial infrastructure is built up, we are planning on adding additional features to AWS and/or the application itself. Our current goal is to develop and implement a Dropbox-style file storage app or use an existing solution. For that we need to research and implement several key things using PHP, JavaScript, or other language:
* Create folders in the s3 bucket based on usernames 
* Upload files into the specific s3 folders 
* Use an API to retrieve a list of available files and display in broswer
* Use an API to download the file from s3
* Follow security proceedures so that other users' folders are inaccessible

The AWS SDK for PHP has the necessary API and methods for data manipulation with s3. I will need to do a lot of research to learn how to implement the solution. The methods are fairly selfexplanatory.
```
S3::putObject(S3::inputFile($tmpfile), AWS_S3_BUCKET, 'path/in/bucket/'.$file, S3::ACL_PUBLIC_READ);
```
There is the file name, bucket name, and path/to/file. I can use the PHP $TOKEN with the username to create a unique path to file for each user.

If all fails are we are unable to fully implement our idea, we have a fallback. OwnCloud is a opensource package for cloud storage and collaboration.

https://aws.amazon.com/marketplace/pp/Bitnami-ownCloud-Certified-by-Bitnami/B00NNZTKJ6

It is available as a container on the AWS marketplace and can be easily set up on an EC2 instance. We can use this service as an example and dissect its code in order to use in our own implementation. 
