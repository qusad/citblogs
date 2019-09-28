---
layout: "post"
---

Continuing with Ansible was fun. I spent a great deal of time on the Ansible Wiki looking up different modules and features. I found it interesting that everything can still be done with shell commands through Ansible. I wonder about the performance between using modules and straight up shell commands. 

I tried battling with Ansible regex file editing and was defeated at the end. I resorted to using the copy module to copy pre-made config files from a folder to their end destinations. One of the problems which I realized later is that lineinfile module will only replace the last match found in a file. One of the config files has same config options for various hosts, which may have been the actual issue, not regex. 

Prometheus was less interesting as it was a fairly simple monitoring tool. I didn't have any issues. My only question is the way processes attach themselves to exposed ports on docker. I have bound the 9090 and 9100 ports but did not specify Prometheus and Node Exporter to use them. I wonder if those are their default ports or if they bind to first available ports. Google search state that those are regular UDP ports. 
