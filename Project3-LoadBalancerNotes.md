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
- 


