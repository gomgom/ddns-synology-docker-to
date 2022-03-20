# DDNS Docker Image for Synology NAS (ddns-synology-docker-to)

[![GitHub license](https://img.shields.io/github/license/gomgom/ddns-synology-docker-to)](https://github.com/gomgom/ddns-synology-docker-to/blob/master/LICENSE)
![GitHub stars](https://img.shields.io/github/stars/gomgom/ddns-synology-docker-to)
![GitHub forks](https://img.shields.io/github/forks/gomgom/ddns-synology-docker-to)

**This Docker package will notify your IP periodically to your Domain Name Server from your Synology NAS.**

This is my repository to share my DDNS Docker Image from Synology to specific Domain Name Server.  
You should prepare your own domain.

If you can modify Dockerfile, you can fix that Dockerfile for fitting to your system.

## Currently Supported Domain Name Server

[![AWS Lightsail Supported](https://img.shields.io/badge/AWS%20Lightsail-supported-yellow)](https://aws.amazon.com/lightsail/)

## How To Use

### **0. Before Use**

1) Go to DSM page of your Synology, Go to 'Package Center'.  
![A image of Package Center](https://user-images.githubusercontent.com/16635223/159150186-b43a37c9-92ef-4d26-b624-7a7ed0c5bb3f.png)

2) Find 'docker' and install that package.  
![A image of Docker Package](https://user-images.githubusercontent.com/16635223/159150136-2256af40-b6fe-4922-875a-3fafb54da136.png)

3) Run 'Docker' after you install package.  
![A image of Docker Icon](https://user-images.githubusercontent.com/16635223/159150307-22a6a416-1bdc-4019-a9fd-001a43992a13.png)

### **1. Easy Way**

1) Go to 'Releases' of this Github page.

2) Download tar.gz file that you want to use.

3) Go to your DSM's docker, go to 'Image > Add > Add From File'  
![A image of Adding Image 1](https://user-images.githubusercontent.com/16635223/159150361-639b8eb6-0236-48e5-bce0-c1b4acf1b87f.png)

4) Go to 'Upload > Browse' and choose that you downloaded tar.gz, if done, click 'Choose'.  
![A image of Adding Image 2](https://user-images.githubusercontent.com/16635223/159150397-8f45f277-28a1-4406-abed-97232f4c9772.png)

5) If done, click the image that you uploaded. Then click Run.  
![A image of Runnling Image 1](https://user-images.githubusercontent.com/16635223/159150435-8f90e179-870c-43fc-a172-afdb9165fde0.png)

6) Make your own container name, and click 'Advanced Setting'.  
![A image of Runnling Image 2](https://user-images.githubusercontent.com/16635223/159150460-27dbf275-af56-47c6-a6fa-d1d64520d864.png)

7) [OPTIONAL] If you want to make this container reboot automatically, choose that option.  
![A image of Runnling Image 3](https://user-images.githubusercontent.com/16635223/159150494-1a1f8a09-04b9-4c1a-8143-47a34a3e52e5.png)

8) Go to 'Environment', Change all of options for customizing, except PATH.  
![A image of Runnling Image 4](https://user-images.githubusercontent.com/16635223/159150482-195f0985-6899-47d7-b416-39034d38601e.png)

9) If you done, click Accept. It should works well. You can check on 'Container'.  
![A image of Containers](https://user-images.githubusercontent.com/16635223/159150552-4cdb3ae9-5b83-40d7-b344-83162358154e.png)

### **2. Advanced Way (If you can use Dockerfile)**

If you can use and change Dockerfile. Just download Dockerfile on the directory and change Dockerfile's setting.

After that, Make image and run on your NAS SSH.

## Customizeing For **AWS Lightsail DNS** [![SUPPORTED](https://img.shields.io/badge/SUPPORTED-yellow)](https://aws.amazon.com/lightsail/)

**For using AWS Lightsail DNS CLI, you should prepare IAM User with AWS Lightsail API permission.**  
You needs AWS Lightsail IAM privileges: **GetDomain, UpdateDomainEntry**  
And also, you need to register your domain and make an A record that you want to use on Lightsail DNS.  
For more information, go to [AWS API page](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html).

1. **ACCESS_KEY_ID = write_your_access_key_id**  
You should write your IAM's Access Key ID.

2. **SECRET_ACCESS_KEY = write_your_secret_access_key**  
You should write your IAM's Access Key ID (it's generally more longer).

3. **ENV DOMAIN_NAME = mydomain.net**  
Please write your domain. You should register your domain on AWS Lightsail DNS.

4. **ENV RECORD_NAME=example.mydomain.net**  
Please write your A record name. You should register A record first time with any other IP.  
Because it just fix your record.

## Questions & Bugs & Etc

If you have any problem to use this application, please tell me your problem on [GitHub Issues](https://github.com/gomgom/ddns-synology-docker-to/issues).  
But please forgive me for poor programming skills because I'm a hobby programmer. :)

Please use freely at your own risk. It's totally OK that you can change this code! But please **just mark who made this**! :D
