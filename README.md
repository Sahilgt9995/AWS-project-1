# Hosting a simple static website using s3 bucket 
Setting up simple static website using AWS as a cloud provider. Using S3 bucket to store and serve the website.
# About project
This project will teach you how to configure s3 bucket for web hsoting and use amazon route 53 for DNS.
# Steps: -

__Step 1: Create an S3 Bucket for Website Hosting__

Log in to your AWS Management Console.

Go to the Amazon S3 service.

Click the "Create bucket" button.

Choose a globally unique name for your bucket (e.g., "my-static-website"). This name will be part of your website URL, so make it relevant to your project.

Select the region where you want to create the bucket.

Leave all other settings as default and click the "Create" button.

__Step 2: Upload Your Website Content__

Inside your newly created S3 bucket, click the "Upload" button.

Select the HTML, CSS, JavaScript, and any other files that make up your website and upload them to the bucket.

Make sure the HTML file you want to serve as your website's main page is named "index.html" (S3 will use this as the default document).

__Step 3: Configure S3 Bucket for Website Hosting__

Go back to your S3 bucket and select it.

Click the "Properties" tab.

Scroll down to the "Static website hosting" section and click the "Edit" button.

Select the option "Use this bucket to host a website."

In the "Index document" field, enter "index.html" (or the name of your main HTML file).

You can configure optional error documents and redirection rules as needed.

Click the "Save changes" button.

__Step 4: Set Permissions for Your S3 Bucket__

In the same "Properties" tab of your S3 bucket, scroll down to the "Permissions" section.

Click on "Bucket Policy."

Add a bucket policy that allows public read access to your objects. Here's an example policy:

{
   "Version":"2012-10-17",
   "Statement":[
      {
         "Sid":"PublicReadGetObject",
         "Effect":"Allow",
         "Principal":"*",
         "Action":[
            "s3:GetObject"
         ],
         "Resource":[
            "arn:aws:s3:::your-bucket-name/*"
         ]
      }
   ]
}

Replace "your-bucket-name" with the name of your S3 bucket.

Click "Save changes" to apply the policy.

__Step 5: Configure Amazon Route 53 for DNS__

Go to the Amazon Route 53 service.

In the Route 53 dashboard, click "Hosted zones" on the left sidebar.

Create a new hosted zone by clicking the "Create hosted zone" button.

Follow the wizard to create a new domain or use an existing one. If you're using an existing domain, you'll need to update your domain registrar's DNS settings to use the Route 53 nameservers.

Once your hosted zone is created, you'll see a set of name servers. Update your domain's DNS settings at your registrar to use these Route 53 name servers.

__Step 6: Test Your Static Website__

Wait for DNS propagation, which can take some time (up to 48 hours, but usually much less).

After DNS propagation, you can access your website using the domain name you configured with Route 53 (e.g., www.yourdomain.com).

That's it! You've successfully set up a simple static website using Amazon S3 for hosting and Amazon Route 53 for DNS. Your website should now be accessible to the public via your domain name.