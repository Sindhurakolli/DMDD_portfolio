---
layout: default
---




# The Cloud

For the purpose of extending and scaling the project a cloud service was very much essential. Through the cloud platform the following were achieved
- Leverage Cloud platform services
- Faster Access using virtual environment
- scalibility of existing resources 

which also had the following advantages 
- Quick Colloboration 
- Lessen the data vuinerability, than on the local 
- Flexibility 

To achieve the purpose we experimemted on using different cloud services like AWS, Azure and Google cloud. We finally settled on using  Google cloud platform as per our requirement, we chose GCP over AWS because of cost factors and also as we had credits for GCP.

Cloud  Requirement Analysis for the Dry Run
The Analysis of cloud and its servies was analysed based on the following features:- 
1 Cloud SQL Instance for Database
 
<br> SQL Standard 
<br> M/C type : db-n1-standard-4
<br> RAM(GB) : 15
<br> Max Storage Capacity: 10,230 GB
<br> Max Connections: 4000

To accomplish the task the following services were to be setup in the cloud environment

### IAM Role

In this service the responsibilities were assigned to the users based on the roles and the the purpose the user is accessing the cloud service. There are three types of roles which are a collection of permissions we  can impose on a user. The following are the roles  
- Primitive roles: Owner, Editor, Viewer
- Predifined roles: Pub/ Sub Publisher
- Custom roles

<screen shot>

### Cloud Storage

In the Google cloud platform, buckets are created to hold objects. To meet the requirement of this project, a bucket named Capsule-networks-project was created to store all the images which were created using Maya. The bucket has folders which the category and subcategory in the way they are stored in the drive

[Drive Link](https://drive.google.com/drive/u/1/folders/1c7wjh__WL8cVYCPE3ebdM8oSq1riKts6)

![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image2.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image5.png)

### Google SQL

For integrating the sql in the cloud a sql servivce was established which is also used for the website.
 
We will require Cloud type as : My SQL and Second Generation.
 
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image1.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image3.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image4.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image6.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image7.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image8.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image9.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image10.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image11.png)

### Google Compute Engine

The compute engine is used for running the neural networks which will reduce the run time. The requirement of the engine is as follows
 
M/C type: n1-standard-8
Virtual CPU: 8
Memory: 30 GB




Please click on below link to go to the website details, overall citations and references and Licence.

* * *

[The Website](./website.html).

* * *

[Back](./)
