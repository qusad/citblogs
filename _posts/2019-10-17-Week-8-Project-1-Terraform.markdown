---
layout: "post"
---

The first real project is looking real good. I am learning a great deal about Terraform and AWS. I like terraform a lot better than Ansible, due to the fact that it has much better error checking and descriptions. I had over 20 errors in my first code, but Terraform showed every error, explained it, and suggested a solution. It looks me no more than 5 minutes to troubleshoot hundreds of lines of code as opposed to a single error in Ansible. It looks like Terraform is also space and tab sensitive, which was half of my issues. 

I was surprised to see that my code did everything it was supposed to from the first try, even though I'm not sure it is 100% correct. The only issue I have encountered is with AWS credentials. I need a user account to access AWS services, but we need to use Terraform to create user accounts. This put me into an infinite logic loop and I've decided to just make a test account for the time being. My next step is to understand how to create the bastion jump instance and how to provision instances located in a private subnet. Ansible works off of public IPs and I will need to learn how to have it access private networks. 

Not going to lie, but I've learned more in these 8 weeks than I have in my last 5 years of university. I'm thoroughly enjoying this class and looking forward to future projects. 
