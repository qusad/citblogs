---
layout: "post"
---
This week was wild for me. Every single class decided to have all the midterms and projects due the same week. For the project itself we set up the rest of the infrastructure: IAM, Security groups, DNS, SSL Certs, and the Load Balancer. We have not applied the new parts to the live server as we do not want to break everything before the presentation. For now we have manually installed the web-server and put Jekyll on it as a proof of concept. After the presentation we will work on implementing the new features.

One big problem that I ran into has to do with the size of the instances. We are using the t2.micro free tier instances which have less than 1GB of RAM. Unfortunately many of the open-source apps require more than that to run. The Flarum app recommened in the project requires over 600mb of RAM for Composer to install everything. This tells me that the app is fairly big in size and resources or Composer is grossly unoptimized. There are plenty of ways to do incremental installation, swap files, or other ways to reduce memory usage for installing/unzipping resources, but Composer doesn't seem to care.
