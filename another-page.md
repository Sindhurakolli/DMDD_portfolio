
# THE DATABASE

Description: This is a report about the database work we have done

The primary task was to create the database with all the image properties, which the understaning how python reads an image file and understand how to stire the image in the database.

Initially, a python script was created to get just one image property. That anyone can look up for any 3D image shots captured using Maya from the database.
The initial script we created got us the properties of just one image using OpenCV imported as cv2. 
OpenCV (Open Source Computer Vision Library: http://opencv.org) is an open-source BSD-licensed library that includes several hundreds of computer vision algorithms.This package is used to extract all the image properties.

The code below is the snippet to grab the image properties.

```python
import numpy as np 
import cv2
cv2.imread('.../Desktop/Capture.png')
print('Image shape is \n', img.shape)
print('Image shape is \n', img.size)
print('Image datatype is \n', img.dtype)
```

The next step to get the data of the images is to loop all the images in a folder and grab the image properties to store it to .CSV
One main constraint is the way how the images are stored in the csv. Initially the idea was save the image path in the database which dose not complete the requirement of creating an image database. To overcome this, the images are stored in BLOB (Binary Large objects).
BLOB is a collection of binary data which is generally of an image or an audio file wchich is stored as a single entity in a database system. 

```python
import pandas as pd
import numpy as np
import cv2
import os
import os, os.path
photos = []
for filename in os.listdir('.../Desktop/photos'):
   photos.append(filename)
file_name = []
shape = []
size =[]
img_type = []
for i in range(0,len(photos)):
   fn = '.../Desktop/photos/{}'.format(photos[i])
   file_name.append(fn)
for i in file_name:
   img = cv2.imread(i)
   shape.append(img.shape)
   size.append(img.size)
   img_type.append(img.dtype)
   image_df = pd.DataFrame(np.column_stack([photos,shape,size,img_type]), 
   columns= ['file_name','shape_1','shape_2','shape_3','size','type'])
image_df.to_csv (r'.../Desktop/image.csv', index = None, header=True)

```
The below code snippet is used to convert the image file into blob.

``` python
#filename = the filepath along with the image name.

def convertToBinaryData(filename):
    #Convert digital data to binary format
    with open(filename, 'rb') as file:
        binaryData = file.read()
    return binaryData
```

The final result is stored into a CSV which is later imported into the database schema.

#### Conceptual Schema


Below is the initial conceptual database schema:


![Octocat](https://raw.githubusercontent.com/Sindhurakolli/DMDD_portfolio/harini/hiii.png)

Later, we came up with few modifications to the schema to add more attributes related to the image.

![Octocat](https://raw.githubusercontent.com/Sindhurakolli/DMDD_portfolio/master/DB_Schema.png)

The above schema can be explained with an example below:


<br> category - table 
<br> category_id: C01 (PK) 
<br> category_name: Animals 


<br> sub_category - table
<br> sub_category_id: C01 (PK)
<br> category_id: C01_01 (FK)
<br> sub_category_name: Dog


<br> sub_category_object - table
<br> object_id: C01_01 (PK)
<br> sub_object_id: C01_01_01 (FK)
<br> object_name: labrador


<br> image_data - TABLE
<br> image_id: I01 (PK)
<br> object_id : (FK)
<br> image_shape: (height, width, length)
<br> image_size: in KB
<br> image_resolution: 960X540
<br> image_type: .png
<br> X: angle in degree
<br> Y: angle in degree
<br> Z: angle in degree
<br> sh_id: sh_01
<br> sa_id: sa_02
<br> bk_id: bk_01
<br> image: BLOB image

A physical database on MYSQL Workbench.

To establish a connection with the MYSql workbench from python, the following script is run to create a connection. This will enable the user to directly connect to the database environment and import the files created directly into the database. 

Code snippet for connecting the database is as follows

```sql
ALTER USER 'root'@'localhost'
 IDENTIFIED WITH mysql_native_password
 BY 'password';
```

```python
import mysql.connector
from mysql.connector import errorcode
try:
  cnx = mysql.connector.connect(host= 'localhost',
                                user='root',
                                password='password',
                                auth_plugin='mysql_native_password',
                                database='images')
  if cnx.is_connected():
            print('Connected to MySQL database')
except mysql.connector.Error as err:
  if err.errno == errorcode.ER_ACCESS_DENIED_ERROR:
    print("Something is wrong with your user name or password")
  elif err.errno == errorcode.ER_BAD_DB_ERROR:
    print("Database does not exist")
  else:
    print(err)
else:
  cnx.close()

```
Challenge faced during the connection establishment is regarding the password authentication with the local host for which the user has to be identified with mysql_native_password on workbench using the below query.

# Few of the Usecases

1. Get all images with certain angles
2. Get all images of certain category
3. Get image properties of the selected image
4. Get 3D image model of particular category
5. Get images of objects within a range of angles


# The Cloud Part

We are using Google cloud platform as per our requirement, we chose GCP over AWS because of cost factors and also as we had credits for GCP

Cloud  Requirement Analysis for the Dry Run
The Analysis of cloud and its servies was analysed based on the following features:- 
1 Cloud SQL Instance for Database
 
<br> SQL Standard 
<br> M/C type : db-n1-standard-4
<br> RAM(GB) : 15
<br> Max Storage Capacity: 10,230 GB
<br> Max Connections: 4000
 
We will require Cloud type as : My SQL and Second Generation.
 
1 Cloud Storage
 
1 Compute Engine Instance
 
M/C type: n1-standard-8
Virtual CPU: 8
Memory: 30 GB

![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image1.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image2.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image3.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image4.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image5.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image6.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image7.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image8.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image9.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image10.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image11.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image12.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image13.png)
![Octocat](https://raw.githubusercontent.com/Preethamalladu/DMDD-Presentation/master/image14.png)



[back](./)
