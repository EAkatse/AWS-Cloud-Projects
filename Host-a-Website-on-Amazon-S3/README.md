<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** Emmanuel Elom Akatse  
**Email:** e.akatse@gmail.com

---

![Image](http://learn.nextwork.org/thankful_white_quiet_troll/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to host a website (make it publicly accessible on the internet) using Amazon S3 (Amazon Simple Storage Service).

I am doing this project to learn how to use Amazon S3 to store and retrieve data when needed, as well as to store my pictures and files, particularly for the website I want to host.

### Tools and concepts

Services I used were mainly Amazon Simple Storage Service (S3). Key concepts I learnt include how to configure an S3 bucket for web hosting, Enabling and understanding Access Control Lists (ACLs) for managing object permissions and Bucket Policies for a broader control, understanding S3 bucket naming conventions ad global uniqueness, Configuring static website hosting on Amazon S3 and understanding the purpose of a bucket website endpoint, Understanding and troubleshooting common errors like "403 Forbidden" during website deployment, Making website files publicly accessible to allow internet users to view your site, and the importance of deleting resources after completing a project to avoid unexpected charges.

### Time, challenges, and wins

This whole project took me approximately one hour to complete. I faced no major challenges during the course of the project. The most rewarding part was documenting the entire process, as it exposed me to new concepts and gave me a different perspective on tasks such as hosting a static website on S3, as well as understanding the difference between ACLs and bucket policies and when to use them effectively.

---

## How I Set Up an S3 Bucket

### What I did in this step

In this step, I will create a bucket (an object container that helps to organize and manage data and files) within S3.

### How long it took to create the bucket

Creating an S3 bucket took me a about 5 minutes. It was a simple and straightforward process.

### Region selection

The region I chose for my S3 bucket was US East (N. Virginia) (“us-east-1”) because it was the first region created in AWS, established in 2006. It is also generally considered one of the cheaper regions compared to others, although the potential costs associated with outages can outweigh those savings.


### Understanding bucket name uniqueness

S3 bucket names are globally unique! This means no two buckets can have the same name, similar to how domain names work. This design simplifies access and management, especially since S3 is widely used for hosting public content (which is the purpose of this project) and needs to avoid conflicts across different users and regions.

![Image](http://learn.nextwork.org/thankful_white_quiet_troll/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### What I did in this step

In this step, I will download all the necessary files for the website and upload them to the bucket, because these files, no one will be able to view or access the site publicly.

### Files I uploaded

I uploaded two files to my S3 bucket - they were an HTML file that sets up the website and an unzipped folder containing images for my website.

### How the files work together

Both files are necessary for this project because the HTML file is serves as the main webpage that users will access, while the images folder contains visual elements that enhance the website’s appearance. Both are required to create a complete static website, as the HTML file references the images to display them correctly on the page.

![Image](http://learn.nextwork.org/thankful_white_quiet_troll/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

### What I did in this step

In this step, I will be configuring my s3 bucket for static website hosting because it configures the S3 bucket to serve my static files directly to web browsers, allowing users to access my website through a unique web endpoint. This setup eliminates the need for traditional server management while providing scalability and reliability for the website.

### Understanding website hosting

Website hosting means making your website public on the internet. It involves storing your website's files (like HTML files and other assets) on a web server and making them accessible online to anyone with the website's URL.

Even if you create a perfect HTML file, it remains a local file on your computer until it's hosted. By configuring a service like Amazon S3 for hosting, you're essentially telling it to create a URL that will display your uploaded files as a webpage.

### How I enabled website hosting

To enable website hosting for my S3 bucket, I first had to configure the bucket’s Static Website Hosting feature.

To do this:

1. Click “Properties” under the name of your target bucket.
2. Scroll down until you see “Static website hosting.”
3. Click the Edit button next to it.

This will open the “Edit static website hosting” page. Then:

4. Enable Static website hosting.
5. Select “Host a static website” as the hosting type.
6. Specify the default (home) page by entering “index.html” as the Index Document.
7. Click “Save changes” to apply all the configurations.

### Access Control Lists (ACLs)

An Access Control List (ACL) is a set of rules and permissions used to manage and grant access to objects within an S3 bucket. It differs from bucket policies, which are also used to manage and control access to an S3 bucket.

So, what’s the difference? ACLs allow you to manage access at a granular level, specifically for individual objects within a bucket, while bucket policies control access at the bucket level, providing broader, more centralized access management.

For this project, I enabled ACLs to better understand how they work in practice.

![Image](http://learn.nextwork.org/thankful_white_quiet_troll/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

### Understanding bucket endpoint URLs

Once static website is enabled, S3 produces a bucket endpoint URL, which is like a regular website URL. It allows people to visit and view your Amazon S3 bucket's files as a website.

### What I saw when I tested the endpoint

When I first visited the bucket endpoint URL, I encountered a “403 Forbidden” error. The reason for this error was because although my website was being hosted on S3, the HTML and image files were still private. To resolve this issue, I needed to set the permissions of the objects to public.

![Image](http://learn.nextwork.org/thankful_white_quiet_troll/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

### What I did in this step

In this step, I will need to make the files publicly accessible so that anyone on the internet can view or download them. For my website to be visible to others, the files that make up the website (such as my HTML and image files) need to be publicly accessible because, by default, Amazon S3 keeps objects private for security reasons. If my website files remain private, visitors will not be able to load my website in their browsers, resulting in an error.

### How I resolved the 403 error

To resolve this 403 Forbidden error, I had to go back to the S3 bucket I created and select the “Objects” tab.
I then selected the checkboxes next to my “index.html” file and the folder containing the website assets.
From the Actions dropdown, I chose “Make public using ACL.”
Once the green banner appeared, I clicked “Close.”
Finally, I returned to the browser tab displaying the 403 Forbidden message, refreshed the page, and the issue was resolved.

![Image](http://learn.nextwork.org/thankful_white_quiet_troll/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

### What I did in this extension

In this project extension, I am about to set up a bucket policy that prevents people from deleting my index.html file and test it to ensure the policy works.
I am doing this to better understand how S3 bucket policies work.

### Understanding bucket policies

An alternative to ACLs are bucket policies, which are also used to manage and control access to S3 buckets at a bucket level (the bucket as well as its contents are affected). The benefit of using bucket policies is that it makes it easy to define and manage permissions for multiple users and actions in a centralized and scalable way, while ACLs are useful for setting simple, object-level permissions for individual files or specific access cases.

![Image](http://learn.nextwork.org/thankful_white_quiet_troll/uploads/aws-host-a-website-on-s3_sm2sm2sm)

### What my bucket policy does

My bucket policy prevents everyone from deleting files from my S3 bucket. I tested this by attempting to delete the “index.html” file from within my “nextwork-website-project-elom” bucket and found that the action was denied. This is because, in the policy, I specified that any request to delete objects in the bucket should be denied for everyone, including myself.

---

---
