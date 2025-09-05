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
```

---

### 4. Run Your Pipeline

1. You can run manually from the Jenkins UI Or automate triggers:
2. Run when code is pushed to GitHub, 
3. Run on a schedule (daily builds), 
4. Run when a pull request is created

---

### 5. Optional Features

1. Parallel builds → run tests for multiple environments at the same time, 
2. Notifications → Slack, email, etc. when build succeeds or fails, 
3. Archiving → save build artifacts or test reports, 
4. Agents / Nodes → add multiple machines to run builds if needed

---

### Summary

1. Install Jenkins
2. Open Jenkins UI → create a job or pipeline
3. Add Jenkinsfile to define steps (build, test, deploy)
4. Run manually or set up automatic triggers
5. Use optional features to make your pipeline more powerful




