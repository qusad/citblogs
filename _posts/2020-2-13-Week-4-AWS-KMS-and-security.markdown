---
layout: "post"
---
Since we are working with AWS, Databases, and user's information, it is important to consider security. AWS provide a wide array of security features within the cloud infrastucture. Our job is to have a secure web application and database. We are already using AWS Key Management Service to encrypt AWS RDS Database's log in credentials during the terraform setup. However, the web server does not have the luxury of using this service. In this case we need to consider other security options. This is the format of the database connection 
```
  $servername = "localhost";
  $username = "username";
  $password = "password";
  $database = "dbname"; 
```

While we can hardcode the variables, it is not very secure. We are planning on setting up the database credentials during the web server installation with ansible. The following module is able to grab the necessary information about an instance and assign it to variables.
```
- rds_instance_info:
    db_instance_identifier: new-database  #name of the database
  register: new_database_info  #assign result to a variable
```

This way we will be able to get necessary information and edit the server files during installation. However, this module cannot access the master password for security reasons. We are also unable to use the AWS KMS service outside of the AWS scope to enter the password. Because of that, the master password may need to be entered manually. For the purpose of the assignemt we can enter it in a text file or pass it through Ansible, but in the real world it will be too unsecure. 
