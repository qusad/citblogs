---
layout: "post"
---
The project is 99% finished. There are only a few last things we need to do. I set up the Lambda functions to turn the servers on, on Friday and turn them off on Sunday. They should turn on in about 2 hours as of the time of me writing this and I will check if it worked. The last thing we need to do is to work on Ansible. We are still having trouble getting the playbook to run against the private servers. Online solutions all steer into the direction of using Dynamic Inventories, but they require extensive setup on the host machine. My preliminary solution is to include a playbook into a playbook. The first playbook will setup the bastion with the necessary security hardening, then at the end will copy a playbook onto the bastion and run it against the 2 private server hosts. 

Now that I think about it. The first solution is probably the only one thats viable. My idea requires more manual work, because the IP addresses are not known until they are created. Or terraform can spit out their IP addresses directly into the ansible hosts file. My other teammate is working on Ansible and I will see what he has to say about this.  

UPDATE: I see that the project talks about Dynamic Inveotories and that has to be the solution. I was able to set up the system using the provided python and ini files. We had to add several new tags to our instances for the scripts to locate them. We were able to successfully scrape the instaces from AWS. Now there is a new problem. Ansible refuses to connect to the instances using ssh, while I can ssh into them with no problems. I have tried all the solutions to the problem without success. Here is the error message for the curious ones.

```
xx.xx.xx.xx | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug1: /etc/ssh/ssh_config line 19: Applying options for *\r\ndebug1: auto-mux: Trying existing master\r\ndebug1: Control socket \"/home/qusad/.ansible/cp/a2465777c4\" does not exist\r\ndebug2: resolving \"xx.xx.xx.xx\" port 22\r\ndebug2: ssh_connect_direct: needpriv 0\r\ndebug1: Connecting to xx.xx.xx.xx [xx.xx.xx.xx] port 22.\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug1: connect to address xx.xx.xx.xx port 22: Connection refused\r\nssh: connect to host xx.xx.xx.xx port 22: Connection refused\r\n",
    "unreachable": true
}
```

I'll be seeking more help online and you can check the progress or find a solution at the link below

<a href="https://stackoverflow.com/questions/58794772/ansible-ssh-connection-error-connection-refused">stackoverflow.com/questions/58794772/ansible-ssh-connection-error-connection-refused</a>
