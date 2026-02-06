```markdown
# Serverless AI Blog Generator 🚀

An event-driven serverless application that uses **Amazon Bedrock (Google Gemini)** to automatically generate high-quality blog posts based on user-provided topics. The system is built for scalability and cost-efficiency, utilizing AWS Lambda, API Gateway, and S3.

## 🏗️ Architecture
The application follows a clean, serverless flow:
1. **API Gateway:** Receives a POST request with a `blogtopic`.
2. **AWS Lambda:** Orchestrates the logic and invokes the AI model.
3. **Amazon Bedrock:** Uses the **Google Gemini (Gemma-3-4b-it)** model via the Converse API.
4. **Amazon S3:** Stores the generated blog post as a timestamped `.txt` file.
5. **Amazon CloudWatch:** Monitors execution logs and performance.

## 🛠️ Tech Stack
- **Language:** Python 3.12
- **AI Model:** Google Gemini (via Amazon Bedrock)
- **Infrastructure:** AWS (Lambda, S3, API Gateway, IAM)
- **SDK:** Boto3 (with Bedrock Converse API)

## 📋 Prerequisites
Before deploying, ensure you have:
1. **Model Access:** Enable **Google Gemini** in the Amazon Bedrock console (Region: `us-east-2`).
2. **S3 Bucket:** Create a bucket named `my-trail-bucket-v1` (or update the code with your bucket name).
3. **Boto3 Layer:** A Lambda Layer containing `boto3 >= 1.34.x` is required for the Converse API.

## 🔐 IAM Permissions
The Lambda execution role requires the following permissions:
- `bedrock:InvokeModel` on the Gemini model ARN.
- `s3:PutObject` on your output bucket.
- `logs:CreateLogGroup` and `logs:PutLogEvents` for monitoring.

## 🚀 Getting Started

### 1. Create the Lambda Layer
```bash
mkdir -p layer/python
pip install boto3 -t layer/python
cd layer && zip -r boto3_layer.zip python
# Upload boto3_layer.zip as a Lambda Layer

```

### 2. Deploy the Code

Create a new Lambda function, attach the layer, and paste the code from `lambda_function.py`. Ensure the timeout is set to at least **1-2 minutes** to allow for AI generation.

### 3. Test the API

Send a POST request to your API Gateway endpoint:

```json
{
  "blogtopic": "The Future of Serverless Computing"
}

```

## 📈 Future Enhancements

* [ ] Implement Prompt Engineering templates.
* [ ] Add support for multi-language blog generation.
* [ ] Integrate a frontend (React/Next.js) for user interaction.
* [ ] Add RAG (Retrieval-Augmented Generation) using Bedrock Knowledge Bases.

## 📄 License

This project is licensed under the MIT License.

```

---

### How to make this "Downloadable"
To provide a direct download link on your blog, you can host this file in your GitHub repository and use the "Raw" link format. It should look like this in Markdown:

`[Download README.md](https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_REPO/main/README.md)`

[AWS Lambda + Bedrock Tutorial](https://www.youtube.com/watch?v=vQ9BUc-UmXY)
This video provides a practical, step-by-step walkthrough of invoking Bedrock from a Lambda function, which is the core of your project's architecture.


http://googleusercontent.com/youtube_content/7

```
