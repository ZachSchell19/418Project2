# Pproject 3 Load Balancer

### starting with gcload
- I first tested the first two gclod commands in the video provided to make sure i was in the right shell.
- I found it neat i couldnt use gcloud commands if I was editing in a VM as well.
### Starting Load balancer 
- I have sat here for a couple minutes and dont know what my defualts are so I am going to just leave them as is and go to the next part
- It made the instance but i am having to delete it becasue any otions for zones are asking for numeric and I am not debating trying to add a default zone
- Issue #3: I was able to use the code to set up the instances but not including the bash my command was as followed
gcloud compute instances create www2 ^
    --zone=northamerica-northeast2-a ^
    --tags=network-lb-tag ^
    --machine-type=e2-small ^
    --image-family=debian-11 ^
    --image-project=debian-cloud
- I had to go into the systems individually and do the following which i found from external resources with the help of google bard, decided to use google ai to help with the code errors on google cloud and it was useful up until this point in writing.
- It has had me go into the system and do 
sud apt-get update 
- from here i am installing apache
sudo apt-get install apache2 -y
- this is now where i am stuck as it is processing triggers.
- It finished! ... 10 mins later.
- I then did a restart and then this
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
- I am saving this for mysefl becasue in task 4 this is all i can get so far
-     IPAddress: 34.130.7.206
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

- I used the external IP from here and then used the powershell to run the loop to test and it at first failed and then i was getting green text and connections.


## Creating the load balancer

-For the first command I had trouble with the system and i had to look up the fact that for the scripting i should use one continuos line and it worked like a charm. I wish i had done that now with the www1,2,3 but live and learn.
- So far now on Task5.4 it has gone smoothly.
- I got the IP 34.144.251.157
- Same with 5.5 and 5.6 the gcloud commands goven are working great

### Task6 testing
I have now done the assignment from Task1-5 and followed the steps however I am unsure if i am supposed to have 2 other insances fully running with ww1,ww2, and ww3. The main only change I had to do was figure out a zone and region and i stuck with the ones that were on my VM's already and also the \ just doesnt work, at all. it has to be ^ or more easy is to just continue on the same line with a space the the '--'. I have 2 insances in my lb-backend-group and they both say running but not healthy. Ive looked it up, Ive waited, Im now just thinking this is why large corporations besides google rarely use google. 


