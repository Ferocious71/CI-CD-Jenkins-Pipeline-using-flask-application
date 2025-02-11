# GitHub Actions CI/CD Workflow
This repository contains a GitHub Actions-based CI/CD pipeline for deploying a Flask application. The workflow includes:

Automated Testing: Runs on every push or pull request to main or staging.
Building the Application: Runs after tests pass.
Deploying to Staging: Triggers when changes are pushed to staging.
Deploying to Production: Triggers when a new GitHub Release is published.
How to Set Up
Fork the repository and clone it locally.
Create main and staging branches.
Add necessary secrets under GitHub repository settings.
Push changes to trigger the pipeline.
Triggering Deployment
Staging: Push to staging branch.
Production: Create a GitHub Release.

Key Section in Your YAML File -
yaml
Copy
Edit
- name: Set up Python
  uses: actions/setup-python@v4
  with:
    python-version: "3.9"
This automatically installs Python 3.9 (or the specified version) on the runner.

How Dependencies Are Installed
Since you already have a requirements.txt file in your repository, the following step in your YAML workflow takes care of installing dependencies:

yaml
Copy
Edit
- name: Install dependencies
  run: |
    python -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt
This:

Creates a virtual environment (venv).
Activates the virtual environment.
Installs all dependencies from requirements.txt.
Conclusion
No need to manually install Python. The YAML file ensures Python is available in the runner before installing dependencies. Just make sure requirements.txt includes all necessary packages for your Flask app. 🚀


# Jenkins CI/CD Workflow


![image](https://github.com/user-attachments/assets/ba012faa-acd0-4c90-be65-402932e8b227)


![image](https://github.com/user-attachments/assets/4bf359b6-6477-4e8e-ac8e-8e81e2e2b0de)

