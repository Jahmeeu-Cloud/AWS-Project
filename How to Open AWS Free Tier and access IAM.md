		

<u>My Project Article</u>


Setting Up a Cost-Effective
AWS Environment for a Small Tech Startup

A.	Introduce the AWS Management Console.

Step 1: Google Search Amazon Web Service (AWS)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i7h3g9jo3vfk65jxrkf4.png)

 

Step 2: Select the with [Amazon](https://www.aws.com)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2qw4u5h0miuilgoedvi6.png)

 

Step 3: Once it open the page like the below image, Select Root


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/uqcqd0kj5h5inwx8z3e4.png)

 



Step 4: Once the Signup page is open, Type your email and follow the procedure by verify and fill in important information and input your card details for confirm.

 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ud9ronc02pf8fdm7o91s.png)




Congratulation, Finally your console page open like this:

 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1jnuaoc6c8glrsgzbotx.png)












B.	Describe the navigation process through different services (EC2, S3, IAM).

C.	Highlight important settings and information.

There are different ways to access these services (EC2, S3, IAM).

Your AWS console dashboard, click on service on right side of the dashboard.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3kypu4wok63l3su4wlh5.png)

 



Go to Service, Select “Security, Identity & Compliance”

  

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/oxj2lxeym8ucy861fj1i.png)



Under Security, Identity & Compliance, check for “IAM” and select IAM.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5l6tfh5tc8ketpjuwapl.png)

 


This is how IAM dashboard.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/n4eeyf18lqi5uuxu5o3y.png)

 

Step on how to access S3.


AWS console Select “Service” Select “Storage”


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9pd2vbw76v2if2cn4kwu.png)




Under Storage select “S3”

 
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nbjuy4vec41gyvz46u5n.png)




This is how S3 dashboard look like.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qn1rwu52s671egnh4b51.png)



How to access “EC2”
Open your AWS console dashboard.
 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jovjuh4n3tyk7q8hbung.png)



Check for “Compute”


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u3uwb13ci6wewjprsmg7.png)



Select EC2


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hya0dpcsydfxg68i6czv.png)





This is EC2 dashboard.
 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qdxg4747q511k4w9qto7.png)




2. Basic IAM Setup


a.	Explain the importance and process of creating an IAM user with privileges
Answer: Creating an IAM (Identity and Access Management) user with privileges is crucial for managing access to AWS resources securely. 

Security: IAM users allow you to grant specific permissions to individuals or applications, reducing the risk of unauthorized access.

Access Control: IAM users enable you to control who can access your AWS resources and what actions they can perform.
Accountability: IAM users provide a clear audit trail, making it easier to track changes and actions taken by users.


b.	Describe the creation of an IAM group for general users and why it’s important.

Open IAM Dashboard
 
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3t0ss71l7f6phpr48i2o.png)




Select User


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u93hgf9a9had9j8gdpd9.png)

 


Under the User, Select “create users”


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zmyslyj3s9s95ryfm20x.png)

 

This is how User dashboard look like:


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8ujmz1hdxgxcx69m1sbf.png)




Type in User name and password you want to use for the User will be type like this and press Next.

 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/khhloioq9tgsgwb1a11a.png)





Then, next page is “set permission and User group” 
 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dmgto4j9qwafhsvj9oww.png)

 



Under Set Permission select “attach policies directly” to give the permission to the user.

 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/06hx56fp2gs7q504jwkl.png)




Choose the permission or type the permission if you know, just like what I did here and click on Next to ”Review and Create”


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fscmk4xdslxv209elnfq.png)

 


Under “Review and Create” confirm the details, once it’s okay you can click on create user.

 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k51o4k1200xi7kxpzy74.png)




Congratulation, You have successfully created a user.
 


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1y35eyzb64zp1ronfevy.png)




c.	Discuss the assignment of basic policies/permissions (e.g. read-only access).

Read-Only access polices is the kind of policies used for certain user and department assigned to monitor and take note of what is happening.



##The END
