  Documentation on Hosting my Static Website Using AWS Amazon S3 bucket

Author: Nzewunwa Grace Onyinyechi
Reg No: AWS/2025/TC4/039

This documentation outlines the process used to host a static webpage on Amazon Web Services (AWS) using an Amazon S3 bucket. It includes creating an HTML file, configuring the S3 bucket, uploading website assets, setting bucket policies for public access, accessing the website through the bucket endpoint, and resolving challenges encountered during the process.


1. Step-by-Step Implementation: Creating the index.html File
I started by building a simple static webpage using HTML.

Steps
Opened a text editor (VS Code).
Created a new file named index.html.
Inserted basic HTML code

    </html>
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nzewunwa Grace O. | Cloud Engineer</title>
    <style>
Saved the file locally.


2. Creating an S3 Bucket: Next, I created an S3 bucket to store and serve the website files.

Steps
Logged into the AWS Management Console.
Navigated to S3.
Selected Create Bucket.
Provided a globally unique bucket name.
Chose a region close to my location.
Disabled Block all public access (required for hosting a public website).
Created the bucket.

3. Uploading the index.html File: With the bucket created, I uploaded the webpage.

Steps:
Opened the bucket.
Clicked Upload → Add Files.
Selected the index.html file.
Completed the upload process.

4. Configuring Bucket Policies and Public Access:
A. Enable Static Website Hosting
Opened the bucket.
Navigated to the Properties tab.
Scrolled down to Static website hosting.
Enabled it.
Set index.html as the index document.
Saved the changes.

B. Add a Bucket Policy to Allow Public Access
AWS requires explicit permission for public access.
I applied the following bucket policy (replacing your-bucket-name with my actual bucket name):

    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Sid": "PublicReadGetObject",
          "Effect": "Allow",
          "Principal": "*",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::gracetech-bucket/*"
        }
      ]
    }

C. Confirm Public Access Settings: Verified Block Public Access settings were disabled.
Checked that the bucket objects (index.html) were marked public.

5. Accessing the Website:
After configuration, I copied the S3 website endpoint URL from the Static Website Hosting section.
I pasted this endpoint into a browser, and the index.html webpage loaded successfully.
This endpoint is the link required for submission.


Challenges and Resolutions
   
Challenge 1:
Access Denied: When Opening the Website
This occurred because the bucket or object was still blocked from public access.

Resolution: Verified that:
"Block all public access" was disabled.
The bucket policy allowed s3:GetObject for all users.
The object itself was public.

Challenge 2:
Bucket Name Already Taken
AWS requires bucket names to be globally unique.

Resolution: Modified the bucket name by adding numbers or unique identifiers.

Challenge 3: Uploaded Files Not Loading
The issue resulted from not enabling static website hosting.

Resolution: Enabled Static Website Hosting and defined index.html as the entry document.


Conclusion

The assignment involved creating an HTML webpage, deploying it to AWS S3, configuring access permissions, and hosting it publicly through an S3 bucket endpoint. After resolving public access and configuration issues, the static website became accessible using the bucket’s website endpoint URL.
The process demonstrates the core workflow of hosting static sites in AWS.
