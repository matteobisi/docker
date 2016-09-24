Inside this readme i describe the folder structure to use the dockerfile to build a was 9 image and configure the cell during the 
image build.

This files was used during my ICONUK 2016 sessions 
(slides available http://www.slideshare.net/mbisi/docker-how-to-deploy-digital-experience-in-a-container-drinking-a-cup-of-coffee )

Inside this project you will be able to find :

>dockerfile
>response file from IBM Installation Manager
>Response file to build the WebSphere cell using manageprofile.sh

To build the image you have to download Was 9 , Was supplements , Java SDK 8  from your IBM Partnerworld profile.

##### Directory listing

This is the folder structure , df-was9 is the dockerfile and sw-repo is the root folder of sw repo
Inside every folder i've put the extracted software

teo@dubuntu:~/docker/was9$ ll


drwxrwxr-x 3 teo teo 4096 Sep 15 18:39 ./
drwxrwxr-x 4 teo teo 4096 Sep 15 17:21 ../
-rw-rw-r-- 1 teo teo 1378 Sep 15 18:39 df-was9
drwxrwxr-x 4 teo teo 4096 Sep  7 10:21 sw-repo/


teo@dubuntu:~/docker/was9/sw-repo$ ll
total 16
drwxrwxr-x 4 teo teo 4096 Sep  7 10:21 ./
drwxrwxr-x 3 teo teo 4096 Sep 15 18:39 ../
drwxrwxr-x 6 teo teo 4096 Sep  7 10:23 was9/
drwxrwxr-x 4 teo teo 4096 Sep  7 10:21 was-sup/


teo@dubuntu:~/docker/was9/sw-repo/was9$ ll
total 24
drwxrwxr-x  6 teo teo 4096 Sep  7 10:23 ./
drwxrwxr-x  4 teo teo 4096 Sep  7 10:21 ../
drwxrwxr-x 10 teo teo 4096 Sep  7 10:23 IM185_LNX64/
drwxrwxr-x  2 teo teo 4096 Sep  7 10:23 RESPONSE/
drwxrwxr-x  5 teo teo 4096 Sep  7 10:23 SDK_JAVA_V8/
drwxrwxr-x  9 teo teo 4096 Sep  7 10:26 WAS_ND_9/

the xml files are the response file obtained from IBM Installation manager to install WAS 9, HTTP, Plugin,
dmgr and appserv01 are the 2 files i used to configure the WebSphere cell

teo@dubuntu:~/docker/was9/sw-repo/was9/RESPONSE$ ll
total 24
drwxrwxr-x 2 teo teo 4096 Sep  7 10:23 ./
drwxrwxr-x 6 teo teo 4096 Sep  7 10:23 ../
-rw-rw-r-- 1 teo teo  557 Aug  2 11:26 appsrv01
-rw-rw-r-- 1 teo teo  384 Aug  2 11:27 dmgr
-rw-rw-r-- 1 teo teo 2134 Jul 11 16:38 was9supp.xml
-rw-rw-r-- 1 teo teo 1197 Jul 11 12:30 was9.xml


teo@dubuntu:~/docker/was9/sw-repo/was-sup$ ll
total 16
drwxrwxr-x 4 teo teo 4096 Sep  7 10:21 ./
drwxrwxr-x 4 teo teo 4096 Sep  7 10:21 ../
drwxrwxr-x 9 teo teo 4096 Sep  7 10:21 WAS9-HTTP/
drwxrwxr-x 9 teo teo 4096 Sep  7 10:21 WAS9-SUPP/
