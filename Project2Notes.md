# Notes For Google cloud Project 2:

### Fedora
 - I have decided to go with Fedora. Nothing against Rocky Linux and I wont lie have have done 0 research into them. I use a different version of Linux on my machine.
 - I chose Fedora because it sounded funny and cool and "Rocky" Linux makes me think this will be a rocky project.
### Setup
- I had trouble at fist connecting with SSH to the first instance i made. i had the region different than my first instance.
- I searched the internet for help, but after 5 minutes I gave up. I just decided to delete the instance and then recreate it in the same region and zone.
- Guess what? It worked. I was shocked.
- Now in with Fedora I started by typing pwd and found i was in /home/me. I messed around after looking up basic fedora commands.
- I first looked up apt vs dnf code defferneces and the google ai automatically poped up a wordpress and linux install. 

- I ignored the site but came back to it after looking up apache fedora install and the site was there again. because it has been about the same up to this point for updating the dnf similar to apt I am hoping this goes smooth.

*I am treating this more like a blog/ notes i do hope that's what it is supposed to be. *

##### Site link here: https://www.liquidweb.com/kb/how-to-install-wordpress-on-linux-almalinux/
-It is for AlmaLinux so we shall see how much or if it messes this up.


### Getting Started
- Got the dnf updated and then proceded to try and connect and it was the default page. I folled the same instructions from the lesson plans to make a new index for myself to make sure it would change.
### database and php
- Now onto installing php and then the database.
- I have got the mariadb installed on my VM and that one was fairly simple and about the exact same as before. PHP I struggled with.
- I intsalled the php library and dependinces and then had to go back and install these seperatly "[~]$ sudo dnf install php-gd php-curl php-pecl-imagick php-pecl-zip libzip"
- I then restarted the httpd and checked my php and mariadb version and status to make sure it was all running. all good so far.
### Wordpress
- So installing wordpresss was fairly similar and gave me, at first, hope. Thed i found out i had to sintall the wget command becasue i could not find a way around it without physically downloading the files. 
- There is probalbly another ssimple way but installing wget wasnt difficult wither it is the same as installing other packages. I got the site up and rinnuing and for the ownership I found out that instead of the www-data it is 'apache'.
- I did have to use google for the last bit to research and I was nervous making the wordpress instal hoping the test site would load properly. All done now wwith Part 2 and onto part3 :)

I would like to say how much Project 1 helped me feel confident and prepared for this.
