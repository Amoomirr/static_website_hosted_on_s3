# Static_Website_Hosted_On_S3

1. Created S3 Bucket for Static Website
   
Created a new S3 bucket named amir-static-website-project
Set bucket to "Block all public access" = OFF to allow public hosting.
Uploaded index.html and image related to the website.

3. Resolved 403 - Access Denied
   
Applied ACL (Access Control List) to make objects publicly readable.
Enabled "Make public using ACL" on uploaded files.

3. Resolved 404 - Not Found
   
Enabled Static Website Hosting in the bucket's properties.
Specified index.html.

5. Created IAM User with Least Privilege
   
Created IAM user: amir-dev.
Attached a custom IAM policy allowing :-

{
  "Version": "2012-10-17",
  "Statement": [
  
    {
    
      "Sid": "AllowS3UploadAndRead",
      "Effect": "Allow",
      "Action": [
      
        "s3:PutObject",
        
        "s3:GetObject"
    ],
      "Resource": "arn:aws:s3:::amir-static-website-project/*"
    },
    {
      "Sid": "AllowBucketListing",
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::amir-static-website-project"
    }
  ]
}


5 Created a Bucket Policy for amir-dev user to allow putobject but deny deleteobject enforcing least privileage :-

{
    "Version": "2012-10-17",
    "Statement": [
        {
        
            "Sid": "AllowPutObjectOnlyFromThisUser",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::322492479923:user/amir-dev"
            },
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::amir-static-website-project/*"
        },
        {
            "Sid": "DenyDeleteObject",
            "Effect": "Deny",
            "Principal": {
                "AWS": "arn:aws:iam::322492479923:user/amir-dev"
            },
            "Action": "s3:DeleteObject",
            "Resource": "arn:aws:s3:::amir-static-website-project/*"
        }
    ]
}
