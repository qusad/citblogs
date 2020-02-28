---
layout: "post"
---
During creation of the AWS RDS instance, a random endpoint/host is assigned by AWS. Our application uses MySQL and PHP to connect to the AWS RDS and the endpoint has to be available as a variable. Fortunately, there are multiple ways to accomplish what we need. The goal is to grab the endpoint from AWS and assign it to a variable which can then be used in other applications, i.e. Ansible and Terraform. We can use the Ansible module <a href="https://docs.ansible.com/ansible/latest/modules/rds_instance_info_module.html#rds-instance-info-module">rds_instance_info</a> to grab the necessary information and register it to a variable.
```
- rds_instance_info:
    db_instance_identifier: new-database  #database name
  register: new_database_info             #assign output to a variable
```

With this we can extract the endpoint address and port from the output, which I assume will be a JSON file and then further assign it to a variable to then edit the necessary files. 

The next step is to work on the SQL implementation of AWS RDS. We need to create a database and several tables for user data storage for our application. The SQL scripts are completed but we need to test them on live servers. 
