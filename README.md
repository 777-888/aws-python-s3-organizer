# 🐍 Python S3 Lambda Tagger

Event-driven Python Lambda function that tags and logs new S3 uploads.

This project was built to demonstrate AWS Lambda automation using Python. When a file is uploaded to an S3 bucket, the Lambda function is triggered automatically, retrieves metadata like the filename and upload timestamp, and can log, tag, or move the file based on custom logic.

---

## 🚀 Features

- ✅ Written in **Python**
- ✅ Triggered by **S3 `ObjectCreated` events**
- ✅ Extracts the object's name and timestamp
- ✅ Logs metadata to **CloudWatch**
- ✅ Easily extendable: tag objects, move them, rename them

---

## 📦 Tech Stack

- **AWS Lambda** (Python 3.x)
- **Amazon S3** (Trigger source)
- **IAM Role** with least privilege
- **CloudWatch Logs**
- **boto3** AWS SDK for Python
- **Tested in Jupyter, deployed via Lambda Console**

## 📄 Sample S3 Trigger Event (test_event.json)

```json
{
  "Records": [
    {
      "s3": {
        "bucket": {
          "name": "your-bucket-name"
        },
        "object": {
          "key": "example-file.txt"
        }
      }
    }
  ]
}
🔧 Deployment

Zip your Lambda function:
zip lambda_function.zip lambda_function.py
Upload to Lambda in AWS Console
Set handler to:
lambda_function.lambda_handler
Assign IAM role with permissions:
s3:GetObject, s3:PutObject, s3:ListBucket, s3:CopyObject
logs:CreateLogGroup, logs:CreateLogStream, logs:PutLogEvents
Add S3 trigger on object upload (event type: PUT)

🧠 How It Works

A user uploads a file to an S3 bucket
S3 triggers the Lambda function
Lambda reads the object key + timestamp
Optional logic can:
Log the upload time
Tag the object (e.g. upload_date)
Move the object to a folder (e.g. by date)
✨ Example Use Cases

Organizing S3 uploads by date
Tagging files for downstream processing
Archiving or categorizing data as it's uploaded
Logging and monitoring uploads in real time
🙋‍♂️ Author

Tristan Jones
Cloud Engineer | AWS Certified Solutions Architect Associate
GitHub • LinkedIn

🧠 Future Improvements

Auto-foldering files by date (/2025/06/25/)
Add SNS/Slack alerts when files are uploaded
Store file metadata in DynamoDB
Add unit tests and CI/CD via GitHub Actions
