# StaticS3
Project 1: Static Website Hosting with AWS S3
Hosting a static website using Amazon S3 is one of the simplest ways to leverage AWS cloud services. It provides a scalable and cost-effective way to serve static content like HTML, CSS, and JavaScript without the need to manage any servers. This project is essential for demonstrating expertise in AWS storage solutions and content delivery.

Architecture Overview

AWS S3: Stores website files.

AWS CloudFront: (Optional) Enhances performance and security by caching content globally.

AWS Route 53: (Optional) Manages domain name resolution for a custom domain.

Step-by-Step Implementation

Create an S3 Bucket:

Log into the AWS Management Console.

Navigate to Amazon S3 > Create Bucket.

Provide a unique name and select a region.

aws s3 mb s3://your-unique-bucket-name

Enable Static Website Hosting:

Open the Properties tab in your bucket.

Select Enable Static Website Hosting and enter index.html as the index document.

{
   "IndexDocument": { "Suffix": "index.html" }
}

Upload Website Files:

Prepare your static website files (HTML, CSS, JS).

Upload them via the AWS Console or CLI.

aws s3 cp index.html s3://your-unique-bucket-name/ --acl public-read

Set Public Access Policy:

Go to Permissions > Bucket Policy and add:

{
   "Version": "2012-10-17",
   "Statement": [
      {
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::your-unique-bucket-name/*"
      }
   ]
}

Test Your Website:

Copy the provided S3 website endpoint URL and open it in a browser.

Achievement & Business Use Case

Achievement: Efficiently hosted a static website with high availability and zero infrastructure maintenance.

Use Case: Ideal for personal portfolios, product landing pages, and corporate marketing sites.

