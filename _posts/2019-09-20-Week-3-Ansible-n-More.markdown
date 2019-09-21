---
layout: "post"
---
I love Ansible. Its easy to learn, intuitive, the syntax makes sense, until you reach the regex. Regex never made sense to me and still doesn't. In Ansible, finding and replacing text requires regex expressions and I still cannot figure it out. In my case everything I only appeds the text at the end of the file instead of changing the  text. I tried lineinfile, blockinfile, and replace. I got very mixed success and decided to go another route. 

A much simpler approach to edit files is to simply copy over ready-made configs and that is what I decided to use. A simple copy/paste is leagues easier than crazy 3 line long regex. At the end of the day I was able to figure it out. The previous lab has helped me greatly to understand the general structure of setting up the lamp stack and I have just reproduced it with Ansible. It was so easy that I wrote out the code by hand in my other class and it mostly worked without any major edits. 

I am very interested to learn how to deploy Ansible into multiple remote machines as that is what this software is for. I can see how useful it can be for setting up or maintaining servers remotely. Doing things via SSH by hand is not something I see myself doing in the future.
