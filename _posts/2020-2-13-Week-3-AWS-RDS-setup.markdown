---
layout: "post"
---
We have started on the infrastructure to implement the AWS RDS service. It requires a few basic components:  public VPC, at least 2 subnets in different availability zones, and optionally, an EC2 instance to access and manipulate the database. The database can be accessed remotely from any MySQL based client but for the purpose of the assignment, we will keep everything inside AWS. 

We will be using 2 EC2 instances for backend, serving the application and a bastion to access the database for testing, similar structure to our last project. First steps are creating the AWS RDS instance and associating it with the appropriate subnets and EC2 instances for communication. 
```
resource "aws_db_instance" "default" {
  allocated_storage    = 20
  storage_type         = "gp2"
  engine               = "mysql"
  engine_version       = "5.7"
  instance_class       = "db.t2.micro"
  name                 = "nova"
  username             = "admin"
  password             = "${data.aws_kms_secret.rds-secret.master_password}" #Encrypted password via AWS KMS
  parameter_group_name = "default.mysql5.7"
}

resource "aws_security_group_rule" "mysql_inbound_access" {
  from_port         = 3306
  protocol          = "tcp"
  security_group_id = "${aws_security_group.rds-sg.id}"
  to_port           = 3306
  type              = "ingress"
  cidr_blocks       = ["10.0.5.0/24", "10.0.6.0/24", "10.0.7.0/24"] #access to webservers and bastion
}
```

We do not want to hardcode any passwords into the terraform file, therefore we will be using the AWS Key Management Server for encrypting the database password to use in our code.

```
resource "aws_kms_key" "rds-key" {
    description = "key to encrypt rds password"
  tags {
    Name = "my-rds-kms-key"
  }
}

resource "aws_kms_alias" "rds-kms-alias" {
  target_key_id = "${aws_kms_key.rds-key.id}"
  name = "alias/rds-kms-key"
}
```

This code has to preceed the creation of the RDS instance as the key needs to be encrypted and available during the creation of the RDS instance. Then we need to actually encypt the password and pass it into AWS using the following command:
```
aws kms encrypt --key-id <kms key id> --plaintext SAMPLE_PASSWORD --output text --query CiphertextBlob
```
This completes the setup and installation of the AWS RDS instance. The next step is to create the database and necessary tables. AWS RDS does not have any built-in means of manipulating the data inside the database and that can only be accomplished using a MySQL client or SQL scripts. We will be using Ansible to pass SQL script files to the database to create the necessary data infrastructure. 

The next step is to fine tune some of the automation as there are several manual steps in the process which can be automated with the use of AWS, Terraform, and Ansible. 
