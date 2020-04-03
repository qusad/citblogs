---
layout: "post"
---
Amazon Web Services has very recently launched a new service: AWS Detective. Since our project heavily relies on security, I have looked into the service to learn more. This service is made to analyze, investigate, and find security problems in all of AWS services and infrastructure. It collects data about your infrastructure and uses machine learning to determine entry points and other security problems. 
<img src="https://d1.awsstatic.com/re19/Diagram_Detective.93ebed7d2e3452fc03c6496bd7faf5b8f2ef9a6e.png">

This service is great for both preventative measures and post-incident investigations. It helps you comb over logs to find possible problems with the infrastructure before an event happens and will track down the issues in the case of an attack or security problem. This is a brand new service and does not yet have implementation through any 3rd party software, i.e. Terraform. I will try to play around with it once our project is in the end stages. 
