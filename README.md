# Natural Reader - AWS Text-to-Speech Converter

This project is designed to convert `.txt` files uploaded to an AWS S3 source bucket into audio files in `.mp3` format using Amazon Polly. The audio files are then stored in a separate destination S3 bucket. The process is automated using AWS Lambda, which is triggered whenever a new text file is uploaded to the source bucket.

## Project Components

### 1. AWS S3 Buckets
- **Source Bucket**: The S3 bucket where users upload `.txt` files.
- **Destination Bucket**: The S3 bucket where the resulting `.mp3` files are stored.

### 2. AWS Lambda Function
The Lambda function is written in Python and performs the following tasks:
- Retrieves the uploaded `.txt` file from the source bucket.
- Uses Amazon Polly to convert the text to speech.
- Saves the generated `.mp3` file to the destination bucket.

### 3. Amazon Polly
Amazon Polly is the service used to convert the text from the `.txt` files into speech. It supports multiple languages and voices, providing a realistic audio output.

### 4. IAM Role and Policy
An IAM role with the following permissions is required:
- **S3 Read/Write Access**: Allows the Lambda function to read from the source bucket and write to the destination bucket.
- **Polly Access**: Allows the Lambda function to call Amazon Polly for text-to-speech conversion.

## Setup Instructions

### 1. S3 Bucket Creation
- Create two S3 buckets: one for the source (text files) and one for the destination (audio files).
- Note down the bucket names for configuration.

### 2. IAM Role Creation
- Create an IAM role with the necessary permissions:
  - `AmazonS3FullAccess`
  - `AmazonPollyReadAccess`
- Attach the role to your Lambda function.

### 3. Lambda Function Deployment
- Write or upload the Python code for the Lambda function.
- Configure the function to trigger on `s3:ObjectCreated:*` events for the source bucket.
- Set the environment variables in the Lambda function to point to the source and destination bucket names.

### 4. Test the Setup
- Upload a `.txt` file to the source bucket.
- Check the destination bucket for the generated `.mp3` file.

## Usage
1. Upload a `.txt` file to the S3 source bucket.
2. The Lambda function will automatically process the file and generate an `.mp3` file.
3. Retrieve the `.mp3` file from the destination bucket.

