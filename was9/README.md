Inside this readme i describe the folder structure to use the dockerfile to build a was 9 image and configure the cell during the 
image build.

This files was used during my ICONUK 2016 sessions 
(slides available http://www.slideshare.net/mbisi/docker-how-to-deploy-digital-experience-in-a-container-drinking-a-cup-of-coffee )

Inside this project you will be able to find :

>dockerfile
>response file from IBM Installation Manager
>Response file to build the WebSphere cell using manageprofile.sh

To build the image you have to download Was 9 , Was supplements , Java SDK 8  from your IBM Partnerworld profile.
To run the images at the end i suggest
docker run -it -p 9060:9060 -p 9043:9043 -p 9080:9080 -h dmgr.ondemand.com was9:1.1 bash 

##### Directory listing

This is the folder structure , df-was9 is the dockerfile and sw-repo is the root folder of sw repo
Inside every folder i've put the extracted software

teo@dubuntu:~/docker/was9$ ll



df-was9
sw-repo/


teo@dubuntu:~/docker/was9/sw-repo$ ll

was9/
was-sup/


teo@dubuntu:~/docker/was9/sw-repo/was9$ ll

IM185_LNX64/
RESPONSE/
SDK_JAVA_V8/
WAS_ND_9/

the xml files are the response file obtained from IBM Installation manager to install WAS 9, HTTP, Plugin,
dmgr and appserv01 are the 2 files i used to configure the WebSphere cell

teo@dubuntu:~/docker/was9/sw-repo/was9/RESPONSE$ ll

appsrv01
dmgr
was9supp.xml
was9.xml


teo@dubuntu:~/docker/was9/sw-repo/was-sup$ ll

WAS9-HTTP/
WAS9-SUPP/
