# 🚀 GitHub Copilot Self-Service Onboarding Workflow

This repository contains a GitHub Actions workflow designed to automate the onboarding of users to GitHub Copilot within your organization.

## Workflow Overview

The workflow is triggered manually and requires an email address as input. 

⚠️ In the workflow, replace `contoso.com` with your organization's domain name.

It performs the following steps:

### 1. 📥 Checkout Repository
- Checks out the current repository to access workflow scripts and resources.

### 2. ✅ Validate Email Domain
- Ensures the provided email address belongs to the `contoso.com` domain.
- If the email domain is invalid, the workflow exits with an error message.

### 3. ➕ Add User to Copilot
- Sends a PUT request to GitHub's API endpoint `orgs/{org}/copilot/billing/selected_users` to add the user to your organization's Copilot subscription.
- Requires a valid GitHub token (`GITHUB_TOKEN`) with appropriate permissions stored in repository secrets.

### 4. 📧 Notify User
- Sends a repository dispatch event to notify the user that they have been successfully onboarded to GitHub Copilot.

### 5. 🧹 Cleanup
- Performs any necessary cleanup actions after onboarding.

### 6. 🎉 Complete Workflow
- Logs a success message indicating the workflow has completed successfully.

## ▶️ How to Run the Workflow

1. Navigate to the **Actions** tab in your GitHub repository.
2. Select the **Onboard Users to Copilot** workflow.
3. Click **Run workflow** and enter the user's email address (`@contoso.com` domain required).
4. Click **Run workflow** to start the onboarding process.

## 📋 Requirements

- GitHub Actions enabled in your repository.
- A GitHub token (`GITHUB_TOKEN`) with permissions to manage Copilot subscriptions and send notifications.
- Users must have a valid `@contoso.com` email address.

## 🤖 GitHub Copilot Self-Service Onboarding

### Environment Variables

The workflow uses the following environment variables:

- `EMAIL_DOMAIN`: The allowed email domain for onboarding users (e.g., `contoso.com`).
- `GITHUB_ORG`: The GitHub organization name used for onboarding users to Copilot (e.g., `contoso`).
- `GITHUB_TOKEN`: GitHub token with permissions to manage Copilot subscriptions and send notifications. Stored securely in repository secrets as `GITHUB_TOKEN`.

ℹ️ Update these variables in the workflow file `.github/workflows/gh-copilot-onboarding.yaml` as needed.