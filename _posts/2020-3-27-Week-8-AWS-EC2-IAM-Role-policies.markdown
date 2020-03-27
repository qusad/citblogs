---
layout: "post" 
---
For our project our web application requires credentials to access our AWS s3 bucket. One way to accomplish that is by providing the AWS IAM credentials directly in the code. But this method is insecure since the account information is exposed in the web files. A better way to accomplish this is by using an IAM role. AWS services can assume roles, giving them similar account priviliges as IAM users. We can specify which AWS resources can be accessed by the user or service which assumes the role. We can attach a role which allows access to s3 to our EC2 web servers. 
```
resource "aws_iam_role_policy" "test_policy" {
  name = "test_policy"
  role = "${aws_iam_role.test_role.id}"

  policy = <<EOF
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "s3:*"
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ]
}
EOF
}
```
This is the best practice for security for accessing resources on AWS. We are still working on implementing the file upload/download system for our web application. 
