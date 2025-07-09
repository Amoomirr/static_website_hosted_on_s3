# static_website_hosted_on_s3
Static-Website-Hosted-S3
1. Hosted a static HTML website on S3 by uploading web files to a custom bucket. 
2. Resolved 403 Access Denied by making objects public using ACL and 404 Not Found by enabling S3 Static Website Hosting.
3. Created IAM user amir-dev with a custom policy allowing only ListBucket and PutObject for this bucket.
4. Configured a matching bucket policy to allow uploads and explicitly deny DeleteObject, enforcing least privilege and minimizing root user access.
