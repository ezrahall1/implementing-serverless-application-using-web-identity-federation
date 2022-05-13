<h1>Implementing Serverless Application Using Web Identity Federation</h1>

<h2>Description</h2>
Project consists of a simple static website created in AWS. The project provides a step by step guide on how to build the static website and what the end result would look like.
<br />


<h2>Services Used</h2>

- <b>S3</b> 

<h2>Environments Used </h2>

- <b>AWS</b>

<h2>Program walk-through:</h2>
<H3>Step 1 - Create Google API project & client ID</H3>

The first thing I did was to create Google API project using the link below

https://console.developers.google.com/apis/credentials:

<img src="https://i.imgur.com/9qmFE1e.png" height="80%" width="80%" alt="Image 1"/>

I clicked on select a project>new project and entered in PETIDF>click create
<br />
<br />
<img src="https://i.imgur.com/TjmFwat.png" height="80%" width="80%" alt="Image 2"/>
<br />
<br />
I clicked on configure consent screen, as this is where you configure various permissions and access right of the application.

<img src="https://i.imgur.com/IId20CI.png" height="80%" width="80%" alt="Image 3"/>

Select external, then click on create

<br />
<br />
<img src="https://i.imgur.com/gzZEhX5.png" height="80%" width="80%" alt="Image 4"/>
I filled in the app information with the below details, and click save and continue.
<br />
<br />
<img src="https://i.imgur.com/jt5X7rA.png" height="80%" width="80%" alt="Image 5"/>

For the next three sections I left as default.
<img src="https://i.imgur.com/daUR9f1.png" height="80%" width="80%" alt="Image 6"/>


<img src="https://i.imgur.com/wl1Bp2P.png" height="80%" width="80%" alt="Image 7"/>



<img src="https://i.imgur.com/j22DHlG.png" height="80%" width="80%" alt="Image 8"/>

I clicked on the credentials tab, this is where I created the API credentials that my serverless application will use to communicate with the Google identity Provider.

<img src="https://i.imgur.com/KbMfu5I.png" height="80%" width="80%" alt="Image 9"/>

I clicked on create credentials and selected OAuth client ID

<img src="https://i.imgur.com/aJO8szJ.png" height="80%" width="80%" alt="Image 10"/>


I filled out the OAuth client ID information with the below details.

<img src="https://i.imgur.com/7PVXYBP.png" height="80%" width="80%" alt="Image 11"/>

Once created I was presented with my client ID and secret password which I needed to make a note of for later.

<img src="https://i.imgur.com/F1ql4zX.png" height="80%" width="80%" alt="Image 12"/>


<H3>Step 2 - Create cognito identity pool</H3>
In the AWS console I went to Cognito section and clicked on manage identity pools.

Create an identity pool name, expand the authentication providers section click on Google+ and enter in the client ID, click create pool.

<img src="https://i.imgur.com/CiRZmSs.png" height="80%" width="80%" alt="Image 13"/>
<br />
<br />

Click on allow to create these roles.
<img src="https://i.imgur.com/4JoIf1M.png" height="80%" width="80%" alt="Image 14"/>

I noted down the identity pool ID and clicked on go to dashboard.

<img src="https://i.imgur.com/M1bgNkJ.png" height="80%" width="80%" alt="Image 15"/>

From there I moved to the IAM section, clicked on roles, scroll down to find Cognito_PetIDFIDPoolAuth_Role and selected it, clicked on permissions tab then click on attach policies search for PrivatePatchesPermissions, tick the box and select attach policy

<H3>Step 3 - Update app bucket & test application</H3>
In the S3 bucket called webidf-appbucket-yrbll2jyqjxb I download two files called index.html and scripts.js. to my local system. Once downloaded I edited them to include the Google client ID the and Identity Pool ID

I used my static web hosting URL link to test the application.

img src="https://i.imgur.com/cA7uWpT.png" height="80%" width="80%" alt="Image 16"/>

img src="https://i.imgur.com/4HIrQIy.png" height="80%" width="80%" alt="Image 17"/>

In the index document section make sure you have added index.html and error.html in the correct text area, click save changes.
<img src="https://i.imgur.com/agU4L6a.png" height="80%" width="80%" alt="Image 6"/>
<br />
<br />
Scroll down to static website hosting section and make a note of your bucket URL.
<img src="https://i.imgur.com/bCb30OR.png" height="80%" width="80%" alt="Image 7"/>

The next step is to upload some objects to the bucket you have created. In order to do that you would need to scroll to the top of the page and click on objects, then click on upload.

Click on upload, click on add files and add the two html files (index.html and error.html). 
<img src="https://i.imgur.com/AQICKJI.png" height="80%" width="80%" alt="Image 8"/>
<H3>Step 3 – Grant permissions</H3>
The next step is you need to grant permissions to be able to read these objects. You would need to create a bucket policy. Click on the permission tab scroll down to where is says bucket policy click on edit. When entering the policy details remember to update the arn so it is not the same as mine or else it would not work, click on save changes.
<img src="https://i.imgur.com/mlZjKBx.png" height="80%" width="80%" alt="Image 9"/>
Based on the policy you have created you will now see a red banner stating, “publicly accessible”, which means the bucket can be access by anyone.

<img src="https://i.imgur.com/PGbBV1i.png" height="80%" width="80%" alt="Image 10"/>

This shows that I successfully created a static website in AWS
<img src="https://i.imgur.com/c8KFtkW.png" height="80%" width="80%" alt="Image 10"/>

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
