# Upload a file to Amazon S3

This project is to uploading files to Amazon S3 for [gongheung.com](https://gongheung.com).

Includes:
- [Client](https://gongheung-data-sharing.netlify.app/)
  - Get a S3 pre-signed url and upload a file to the S3 bucket
- Server
  - Generate a pre-signed url on Amazon Lambda
 
## AWS

### Amazon S3
#### Bucket policy to generate a pre-signed url
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::bucket-name/*"
        }
    ]
}
```

### Amazon API Gateway
#### CORS configuration
- Access-Control-Allow-Origin: https://website-name.com
- Access-Control-Allow-Headers: Content-Type, X-Amz-Date, Authorization, X-Api-Key, X-Amz-Security-Token
- Access-Control-Allow-Methods: GET, POST, OPTIONS

## Reference
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/PresignedUrlUploadObject.html
- https://www.alter-solutions.com/articles/file-upload-amazon-s3-url
