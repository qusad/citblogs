---
layout: "post
---
I'm starting to like Docker the more I learn about it. Knowing about Docker would've been great in my COMP424 class since we had to create a site which was fully build and automated from a single file. Back then I used bash scripts which worked but were not as effective as a Docker image can be.

During this lab I learned the importance of command layering and containers. I've had several problems where the commands would not run in sequence since I did not chain them properly. Each RUN command runs in its own container and this gave me problems when I tried to run several commands in certain directories. You have to set the WORKDIR or properly chain the RUN commands to accomplish anything in docker. Also layering improves performance and reduces size of the image.

During my exploration of Docker, I found out that different services should be ran in different containers rather than in a single one. I did not fully understand the process and the reason, but hoping that the lectures will explain this concept better.
