# NotesApp - AWS tutorial

This is a hands-on project based on AWS tutorials to build a fullstack React application with Amplify.  

## Initial Setup

1. **AWS SSO and CLI**
   - Configure an SSO session and AWS profile for Amplify. Create a profile (e.g., `profile-name`) and note the `sso_start_url`, `sso_account_id`, `sso_role_name`:
     
     ```bash
     aws configure sso
     ```
   - Login to the profile:
     ```bash
     aws sso login --profile profile-name
     ```

2. **Amplify CLI / Sandbox**
   - Install Node.js and npm if not already installed: [https://nodejs.org](https://nodejs.org)
   - Install Amplify CLI globally:
     ```bash
     npm install -g @aws-amplify/cli
     ```
   - Install `ampx` globally for sandbox:
     ```bash
     npm install -g ampx
     ```
   - Start the sandbox environment using your profile:
     ```bash
     npx ampx sandbox --profile profile-name
     ```

## Development Workflow

- **Frontend:** uses Amplify SDK / DataStore to access the backend.
- **CRUD for Notes:**
  - `data.Note.create({...})` → POST / create
  - `data.Note.query()` → GET / list
- Changes made in the local backend (sandbox) are applied **only when the sandbox is running**.  
- If the sandbox is stopped, the frontend uses the last deployed backend in AWS cloud.

## Notes

- SSO tokens expire after a certain period (usually 1-12 hours), so you need to log in again periodically:
  ```bash
  aws sso login --profile profile-name
