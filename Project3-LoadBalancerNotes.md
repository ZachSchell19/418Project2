# Pproject 3 Load Balancer

# Attempt 1

### starting with gcload
- I first tested the first two gclod commands in the video provided to make sure I was in the right shell.
- I found it neat I couldnt use gcloud commands if I was editing in a VM as well.
### Starting Load balancer 
- I have sat here for a couple minutes and dont know what my defualts are so I am going to just leave them as is and go to the next part
- It made the instance but I am having to delete it becasue any otions for zones are asking for numeric and I am not debating trying to add a default zone
- Issue #3: I was able to use the code to set up the instances but not including the bash my command was as followed:
-
  ```
  gcloud compute instances create www2 ^
    --zone=northamerica-northeast2-a ^
    --tags=network-lb-tag ^
    --machine-type=e2-small ^
    --image-family=debian-11 ^
    --image-project=debian-cloud```
- I had to go into the systems individually and do the following which I found from external resources with the help of google bard, decided to use google ai to help with the code errors on google cloud and it was useful up until this point in writing.
- It has had me go into the system and do 
   ```
   sud apt-get update 
- from here I am installing apache
  ```
    sudo apt-get install apache2 -y
- this is now where I am stuck as it is processing triggers.
- It finished! ... 10 mins later.
- I then did a restart and then this
  ```
    echo "<h3>Web Server: www1</h3>" | sudo tee /var/www/html/intex.html
- I got back the sudo tee writes to the index file and also displayed it on the command line. 
- I repeated this for ww1, ww2, and ww3. I changed the above echo command accordingly.
- Im now on www3 and the install apache still takes a while.
- Now that the instances are set up I will continue following the instructions with the firewall
  
###Firewall
- I got the fire wall set up easily

## Load Balancer

#### Server config

- first things first, knowing the regions helped a lot becasue no default seemed to work and it was a pian figuring out it was 'northamerica-northeast2' when everything else was 'northamerica-northeas2-a'
- Now on sending traffic and running into a couple problems. It is saying IPADDRESS and while are not recognized commands
- I am saving this for mysefl becasue in task 4 this is all I can get so far
 ```
    IPAddress: 34.130.7.206
    IPProtocol: TCP
    creationTimestamp: '2023-12-05T12:48:11.430-08:00'
    description: ''
    fingerprint: i07e8gzNkEo=
    id: '3404877022596575844'
    kind: compute#forwardingRule
    labelFingerprint: 42WmSpB8rSM=
    loadBalancingScheme: EXTERNAL
    name: www-rule
    networkTier: PREMIUM
    portRange: 80-80
    region: https://www.googleapis.com/compute/v1/projects/schellsys-418/regions/northamerica-northeast2
    selfLink: https://www.googleapis.com/compute/v1/projects/schellsys-418/regions/northamerica-northeast2/forwardingRules/www-rule
    target: https://www.googleapis.com/compute/v1/projects/schellsys-418/regions/northamerica-northeast2/targetPools/www-pool
```
- I used the external IP from here and then used the powershell to run the loop to test and it at first failed and then I was getting green text and connections.


## Creating the load balancer

-For the first command I had trouble with the system and I had to look up the fact that for the scripting I should use one continuos line and it worked like a charm. I wish I had done that now with the www1,2,3 but live and learn.
- So far now on Task5.4 it has gone smoothly.
- I got the IP 34.144.251.157
- Same with 5.5 and 5.6 the gcloud commands goven are working great

## Task 6 testing
-I have now done the assignment from Task1-5 and followed the steps however I am unsure if I am supposed to have 2 other insances fully running with ww1,ww2, and ww3. 
-The main only change I had to do was figure out a zone and region and I stuck with the ones that were on my VM's already and also the \ just doesnt work, at all. it has to be ^ or more easy is to just continue on the same line with a space the the '--'. 
-I have 2 insances in my lb-backend-group and they both say running but not healthy. Ive looked it up, Ive waited, Im now just thinking this is why large corporations besides google rarely use google, I get the use of google here, that was a diss on how I dislike google as a whole. 
- I waited an hour an refreshed and still not healthy. I am going to lookup how to fix health on them.
- Using
  ```
  gcloud compute instance-groups set-named-ports lb-backend-group --named-ports http:80 --zone northamerica-northeast2-a
 I was able to set the ports to 80 so thats 1/2 of the problem however the health still has a caution sign while both are running.
 - now for some reason without changing anthing one of my two backend groups went down.
 - it has been restarting and verfing and then restarting again for over an hour. I decided to restart both of them in the group becasue I would have to remove and readd otherwise and now both wont pop back up.

I might have to go back an title this section as Part1 and below here will be Second try. I am taking screenshots of everything up until now and they will be in the word for refrence of what not to do. 

# Attempt 2

##### My plan for this is to delete and restart. I now know the commands better and I am going to give it a second go. I feel more confident and lets not lose this hope
- To not lose hope- I am going to be getting rid of everything except the first 2 projects- just to start fresh.
- 
- for making the 3 instances this was my code
``` gcloud compute instances create wwwlb1 --tags=network-lb-tag --machine-type=e2-small --image-family=debian-11 --image-project=debian-cloud --metadata=startup-script="#!/bin/bash; apt-get update; apt-get install apache2 -y; service apache2 restart; echo '<h3>Web Server: wwwlb1</h3>' > /var/www/html/index.html" ```
- So far I have ran into more problems and I am including screenshots in Errors section on the document to help try and explain my struggles.
- I wont sugar coat anything I have tried to recreate the instances using single line becasue the format of multiline provided didnt work and when I used multiline of ^ it worked 80% of the time. Single line seemed to work to get them running as provided in a picture in the word doc however the website had no notice of several of them and the ones that were deleted still appearing on there.
- I wanted to try one more thing before getting away from this for tonight and to go in to the machines themself and I apparently dont have permissions on my own VM's

## Next day
- It is now the next day and with a fresh set of eyes and a freshly towed car I will now try one last time.
- I can now get into the instances that I made, at least starting with lbwww3 and then going to work my way forward.
- Yet again the code for the bash script did not work so I am making the web pages myself and doing the updates and installs accordingly.
- I am able to skip the firewall rule as it was made in attempt 1.
- When I run the install and update commands without sudo I get permission errors. I wonder if I had added sudo into my code for making them if it would have worked. If I delet again for a last time I will attempt that. It is a strong if I delete.
- I have now made the instances and completed step 4. This time I went to the ip 34.130.7.206 becasue I could not get the code to do the script but going to the IP and refreshing the page would change after every couple of refreshes and some time.
- I got all the way to the web server again and the machines are not healthy. Because the script didnt work on initalizing I am going to go in and perform the script myself.
- I will include picture of my results in the Final section of my word doc as I have gotten the load balancer to display both of the servers page from, however it doesnt display host name or the web server. If you go to the IPAddress from the forwarding rule you will get all 3 variants over time.
- I really dont know what I did wrong but I give myself props for trying. I apologize for the possible roller coaster of emotions.
- Before I finish my word doc and submit I wanted to try assigning the ports on the load balancer becasue it was giving me a warning and now everything is healthy and no marks but the server does not pop up.
