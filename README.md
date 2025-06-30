# Deployment Pipeline to AWS S3 – Project Walkthrough

This project demonstrates how to set up a CI/CD pipeline using **GitHub Actions** to automatically build and deploy a React application to an **AWS S3 bucket**.  
Below, each screenshot in the README is explained in the context of the deployment process, including errors encountered and how they were resolved.

---

## 1. Repository Setup

![1](./img/1.%20repo.jpg)

The project begins with a GitHub repository containing a basic React app structure. This is the foundation for the deployment pipeline.

---

## 2. Creating the GitHub Actions Workflow

![2](./img/2.%20workflow.jpg)

A workflow file is created in `.github/workflows/deploy-to-aws.yml`. This file defines the steps for the CI/CD pipeline, such as checking out code, installing dependencies, building the app, and deploying to S3.

---

## 3. Writing the Workflow Script

![3](./img/3.%20script.jpg)

The initial workflow script is written. It includes steps for checking out the code, setting up AWS credentials, installing dependencies, building the project, and deploying to S3.

---

## 4. Setting Up AWS Credentials in GitHub

![4](./img/4.%20secreat%20and%20variable.jpg)

AWS credentials (`ACCESS_KEY_ID` and `SECRET_ACCESS_KEY`) are securely stored as GitHub repository secrets. This allows the workflow to authenticate with AWS without exposing sensitive information.

---

## 5. Creating the S3 Bucket

![5](./img/5.%20s3.jpg)  
![6](./img/6.%20bucket.jpg)

An S3 bucket is created in the AWS Console. This bucket will receive the deployed files from the workflow.

---

## 6. Updating the Workflow Script

![7](./img/7.%20actual%20updated%20script.jpg)

The workflow script is updated and refined to ensure all necessary steps are included and the correct bucket name is used.

---

## 7. Encountering and Debugging Errors

### Error: Build Directory Not Found

![8](./img/8.%20error.jpg)  
![9](./img/9.%20debug.jpg)

The workflow fails because the `build` directory does not exist. This usually means the React app did not build successfully, often due to missing files or dependencies.

---

### Error: Missing Required Files

![10](./img/10.%20error%202.jpg)  
![11](./img/11.%20solution%202.jpg)

The workflow reports missing required files such as `index.html` or `index.js`. The solution is to ensure that `public/index.html` and `src/index.js` exist in the project.

---

### Error: Module Parse Failed

![12](./img/12.%20error%203.jpg)  
![13](./img/13.%20solution%203.jpg)

A module parse error occurs due to an incorrect `"type"` field in `package.json` or improper use of ES module syntax. The solution is to remove `"type": "commonjs"` from `package.json` and ensure ES module syntax is used.

---

### Error: Missing Dependencies

![14](./img/14.%20error%204.jpg)  
![15](./img/15.%20solution%205.jpg)

The workflow fails because dependencies like `react` and `react-dom` are missing. Adding these to `package.json` resolves the issue.

---

## 8. Successful Deployment

![16](./img/16.%20deployed%20ao%20aws.jpg)

After resolving all errors, the workflow completes successfully and deploys the app to AWS S3.

---

## 9. Verifying the Deployment

![17](./img/17.%20s3%20output.jpg)

The deployed files are visible in the S3 bucket, confirming that the CI/CD pipeline is working as intended.

---

## Summary

This project walks through the process of setting up a GitHub Actions workflow to deploy a React app to AWS S3, including:
- Repository and workflow setup
- AWS credential management
- S3 bucket creation
- Debugging and resolving common errors
- Achieving a successful automated deployment

The screenshots provide a visual guide to each step and the troubleshooting process, making it easier to understand and replicate the setup.

