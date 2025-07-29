# 🧾 Static Website Hosting on Amazon S3 with IAM-Based Access Control

This project demonstrates how to host a static website on **Amazon S3** while implementing secure **IAM-based access control**, following the Principle of Least Privilege.

---

## 📌 Project Overview

- ✅ Hosted a **static website** using S3's static website hosting feature.
- ✅ Enforced **fine-grained access control** using **IAM policies and groups**.
- ✅ Ensured **upload-only** access for IAM users without delete permissions.
- ✅ Resolved common access issues like **403 Forbidden** and **404 Not Found**.
- ✅ Simulated and verified IAM permissions using the **AWS IAM Policy Simulator**.

---

## 🧱 Tech Stack

- **AWS S3** – Static website hosting, object storage, bucket configuration.
- **AWS IAM** – Role-based access control, policies, groups, and MFA.
- **AWS IAM Policy Simulator** – Validated custom IAM policy actions.

---

## 🔧 Key Features

### ✅ Amazon S3
- Static website hosting enabled with `index.html` as landing page.
- Bucket versioning and lifecycle policies explored.
- Public access configured (disabled block public access).
- Object-level metadata and unique key-based file storage.

### ✅ IAM Access Control
- Created custom IAM Policy (`S3-StaticWebsite-UploadPolicy`) allowing:
  - `ListAllMyBuckets`
  - `ListBucket`
  - `PutObject`
  - ❌ Denied `DeleteObject`
- Created IAM Group: `S3-StaticWebsite-Uploaders`
- Created IAM User: `amir` with **MFA enabled**, added to the group.

### ✅ Access Testing
Used **IAM Policy Simulator** to test:
- ✅ `s3:ListAllMyBuckets`
- ✅ `s3:ListBucket`
- ✅ `s3:PutObject`
- ❌ `s3:DeleteObject` (denied by design)

---

## 🔗 Website URL

🌐 [Visit the Website](https://amir-static-website-project.s3.ap-south-1.amazonaws.com/index.html)

---

## 🛡️ Security Practices

- Enforced **MFA (Multi-Factor Authentication)** for IAM user login.
- Followed the **Principle of Least Privilege** for all IAM roles and actions.

---

## ✅ Outcome

- Successfully deployed a static website on Amazon S3.
- Implemented secure and minimal access permissions using IAM.
- Ensured that sensitive operations like object deletion remain denied.
- Validated all actions through the AWS IAM Policy Simulator.

---

## 📁 Files

🧱 Step 1: Architecture Overview
S3 Static Website Architecture Diagram
<img width="1944" height="908" alt="s3-architecture" src="https://github.com/user-attachments/assets/b9111f6a-5240-4a81-8c82-87e429ae982c" />

⚠️ Step 2: Common Errors Encountered
404 Not Found Error due to Missing Index Document
<img width="1055" height="363" alt="Error_404NotFound" src="https://github.com/user-attachments/assets/5d59444a-f599-4f05-8075-3b878bc9ce1c" />


404 Error Solved by Enabling Static Website Hosting
<img width="1521" height="675" alt="404_Solved" src="https://github.com/user-attachments/assets/cbd20e70-5cf2-43ca-892a-64813a98afc4" />

403 Forbidden Error (Access Denied)
<img width="1298" height="372" alt="403Forbidden Error" src="https://github.com/user-attachments/assets/a699d43c-cf53-495b-b27d-ddac9878be41" />

403 Error Resolved with Proper Bucket Policy
<img width="1521" height="762" alt="403_Solved" src="https://github.com/user-attachments/assets/ad1eb365-765f-48a8-af4e-02fb068a379f" />

🔐 Step 3: Access Configuration
Public Read Access Bucket Policy JSON
<img width="813" height="630" alt="S3-Bucket-Policy" src="https://github.com/user-attachments/assets/556d8a8a-f0c3-4bed-84a2-b190b766a45c" />

