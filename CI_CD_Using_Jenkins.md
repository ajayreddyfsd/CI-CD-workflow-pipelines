# Jenkins CI/CD Guide

This is a **simple guide** to perform CI/CD using Jenkins.

---

## 1. Install Jenkins

1. Download and install Jenkins from [https://www.jenkins.io/](https://www.jenkins.io/)  
2. Open Jenkins in your browser (usually `http://localhost:8080`)  
3. Follow the setup instructions to unlock Jenkins and install recommended plugins  

---

## 2. Create a Job or Pipeline

1. Go to Jenkins dashboard  
2. Click **"New Item"**  
3. Choose **Pipeline** (or Freestyle project for simple cases)  
4. Give it a name and click **OK**  

---

## 3. Add Your Code

- Use a **Jenkinsfile** in your project repository  
- Example for a Node.js / React project:

```groovy
pipeline {
    agent any             // Run on any available Jenkins machine
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-repo.git' // Get your code
            }
        }
        stage('Install') {
            steps {
                sh 'npm install' // Install dependencies
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build' // Build the project
            }
        }
        stage('Test') {
            steps {
                sh 'npm test' // Run tests
            }
        }
        stage('Deploy') {
            steps {
                sh './deploy.sh' // Optional: deploy your app
            }
        }
    }
}

---

### 4. Run Your Pipeline

You can run manually from the Jenkins UI Or automate triggers:
Run when code is pushed to GitHub
Run on a schedule (daily builds)
Run when a pull request is created

---

### 5. Optional Features

Parallel builds → run tests for multiple environments at the same time
Notifications → Slack, email, etc. when build succeeds or fails
Archiving → save build artifacts or test reports
Agents / Nodes → add multiple machines to run builds if needed

---

### Summary

Install Jenkins
Open Jenkins UI → create a job or pipeline
Add Jenkinsfile to define steps (build, test, deploy)
Run manually or set up automatic triggers
Use optional features to make your pipeline more powerful


