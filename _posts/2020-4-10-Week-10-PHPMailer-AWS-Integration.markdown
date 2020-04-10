---
layout: "post"
---
Our application includes account creation system which uses PHPMailer add-on for email verification. It is a simple module which allows you to send emails directly from your application to the intended target. We use it to send an email with the link back to the website to authenticate the user. Here is the general format. 

<img src="https://github.com/qusad/citblogs/blob/gh-pages/Capture.PNG">

However, we hit a snag trying to implement this feature on AWS EC2 instances. The email would not send and it took a while to figure out why. We had to dig through both PHP and AWS logs to find the issue. Apparently, by default, each AWS account has the outgoing emails disabled. It makes sense so people do not build mass email spam bots using AWS resources. To get around this issue, we need to contact AWS directly to request the feature to be enabled on our account. From there, they will evaluate our account and reasons for needing the email system, and decide to enable or disable the feature.

In the meantime we can manually add email exceptions to the AWS Simple Email System for testing purposes. This is a great security feature on Amazon's end and makes complete sense after we thought it through. Amazon tries to look at both sides: internal users and external users which are going to be affected by their resources. We won't request the email ban lifted since we do not need it for the purposes of the project. 
