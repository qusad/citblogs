---
layout: "post"
---
<<<<<<< HEAD
This week's assignments have given me a proper headache. I love developing on Linux system, but oh boy the random(or not-so-random) permissions, dependency, and version errors drove me insane. Docker was fairly simple, but required me to try 2 different VMs and my Windows machine to get anywhere. Finding a ready build image helped immensly. However, now I know that you can have a full fledged Linux setup on a Windowns machine without the need for any 3rd party virtualizaion software.

Docker was an interesting item but I did not fully understand the purpose of it in terms of the first lab. The only thing I remember it that I had a 3 layer SSH connection between my VM, CSUN, and back to docker.
=======
This week's assignments have given me a proper headache. I love developing on Linux system, but oh boy the random(or not-so-random) permissions, dependency, and version errors drove me insane. Docker was fairly simple, but required me to try 2 different VMs and my Windows machine to get anywhere. Finding a ready build image helped immensly. However, now I know that you can have a full fledged Linux setup on a Windowns machine without the need for any 3rd party virtualizaion software. 

Docker was an interesting item but I did not fully understand the purpose of it in terms of the first lab. The only thing I remember it that I had a 3 layer SSH connection between my VM, CSUN, and back to docker. 
>>>>>>> e1a44139302bfa37679db247ed416db841381163

Jekyll was the fun part. It took me 4 hours to figure out a 10 minute process due to numerous errors, both of which were my fault and not. The main problem is that Jekyll is currently at version 4 while GitHub only supports 3.8.5 and between those two versions, there are hunders of different dependencies. I had to manually install/change each plugin and gem to the correct version. The link below will have all the correct dependencies GitHub for those who are still having issues.

https://rubygems.org/gems/github-pages

Next one was a plugin which was a dependency of a dependency of a dependency of github-pages. It required very specific libraries which are available by default on MACs but not other distros. The error message and the required libs were hidden in hundreds of lines of code. But for those who need help installing 'nokogiri' use the link below.

https://nokogiri.org/tutorials/installing_nokogiri.html

<<<<<<< HEAD
Lastly, do not select any of the GitHub Jekyll themes, as it completely broke my site. Looking forward to our next assignments.
=======
Lastly, do not select any of the GitHub Jekyll themes, as it completely broke my site. Looking forward to our next assignments. 
>>>>>>> e1a44139302bfa37679db247ed416db841381163
