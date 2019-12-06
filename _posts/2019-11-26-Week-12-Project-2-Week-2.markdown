---
layout: "post"
---
We have chose option 4 for our last project. We will be implementing Backups and Monitoring. These are the two tasks that my other team members will start on. In the meantime I will be optimizing the existing infrastructure and creating more automation. Previously, I was told that some tasks did not need to be automated, when they actually had to. My goal is to setup the host machine in order for it to run the necessary terraform commands. This will cut down the manual setup of terraform, AWS-cli, Dynamic Inventory, and ssh keys. This assumes that the host machine is fresh without the necessary modules and dependencies. This will create redundancy, but will be a smoother process for the user

Currently I am creating an ansible playbook to install terraform, AWS-cli, Ansible Dynamic Inventory, and generate ssh keys. I am using Ansible prompt module to grab AWS credentials via user input and using the ssh-keygen module to create the keys.

```
- openssh_keypair:
    path: /tmp/keypair
    size: 2048
    type: rsa
```

There are a couple of ways of doing user input and the pause/prompt seems the most reasonable. It pauses the execution of the playbook to allow various things to happen, including user input.

```
- pause
    prompt: "Enter a value"
    register: user_input
    delegate_to: localhost
```

This bit of code asks a question, registers it to a variable named 'user_input', and delegates it to the localhost. Delegation is very useful as it can be used to pass variabled to different hosts during execution. 
