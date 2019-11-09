---
layout: "post"
---
The project is 99% finished. There are only a few last things we need to do. I set up the Lambda functions to turn the servers on, on Friday and turn them off on Sunday. They should turn on in about 2 hours as of the time of me writing this and I will check if it worked. The last thing we need to do is to work on Ansible. We are still having trouble getting the playbook to run against the private servers. Online solutions all steer into the direction of using Dynamic Inventories, but they require extensive setup on the host machine. My preliminary solution is to include a playbook into a playbook. The first playbook will setup the bastion with the necessary security hardening, then at the end will copy a playbook onto the bastion and run it against the 2 private server hosts. 

Now that I think about it. The first solution is probably the only one thats viable. My idea requires more manual work, because the IP addresses are not known until they are created. Or terraform can spit out their IP addresses directly into the ansible hosts file. My other teammate is working on Ansible and I will see what he has to say about this.  
