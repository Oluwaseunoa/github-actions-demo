# GitHub Actions CI/CD with AWS Elastic Beanstalk Deployment

Author: Oluwaseun Osunsola  
LinkedIn: https://www.linkedin.com/in/oluwaseun-osunsola-95539b175/  
Project GitHub Link: https://github.com/Oluwaseunoa/github-actions-demo  

This project demonstrates a complete **CI/CD pipeline** for a Node.js application using **GitHub Actions**, **semantic releases**, and **AWS Elastic Beanstalk** for deployment. It includes **99 screenshots** documenting each step of the process.


## Table of Contents

1. [Project Overview](#project-overview)
2. [Prerequisites](#prerequisites)
3. [Project Setup](#project-setup)
4. [Local Testing](#local-testing)
5. [CI Pipeline Setup](#ci-pipeline-setup)
6. [Semantic Release Pipeline](#semantic-release-pipeline)
7. [AWS Setup and Elastic Beanstalk Deployment](#aws-setup-and-elastic-beanstalk-deployment)
8. [Deploy Workflow](#deploy-workflow)
9. [Release and Deployment Verification](#release-and-deployment-verification)
10. [Project Implementation](#project-implementation)

---

## Project Overview

This project sets up a Node.js application with:

* **Express.js server**
* **Mocha** for testing
* **GitHub Actions CI pipeline** for continuous integration
* **Semantic release** for automated versioning
* **Elastic Beanstalk deployment workflow** triggered by releases

---

## Prerequisites

* Node.js v20 installed locally
* GitHub repository created
* AWS account with **Elastic Beanstalk** access
* IAM user with **AdministratorAccess**
* GitHub repository secrets for AWS credentials:

  * `AWS_ACCESS_KEY_ID`
  * `AWS_SECRET_ACCESS_KEY`
  * `AWS_REGION`

---

## Project Setup

1. **Create repository** and initialize with README
2. **Clone the repository** locally
3. **Initialize Node.js project** with `npm init -y`
4. **Install Express**: `npm install express`
5. **Create `app.js`** and add basic server code
6. **Install Mocha for testing**: `npm install --save-dev mocha`

---

## Local Testing

* Write simple test in `test.js`
* Update `package.json` scripts for testing
* Run `npm test` locally to verify functionality
* Start the server locally: `npm start`
* Visit `http://localhost:3000` to verify “Hello, World! This is version 1.0.0”

---

## CI Pipeline Setup

* Create `.github/workflows/ci.yml`
* Steps include:

  * Checkout code
  * Install dependencies
  * Run tests
* Push to GitHub triggers **CI workflow**
* Verify workflow runs successfully

---

## Semantic Release Pipeline

* Install dependencies for **semantic-release**
* Configure `.releaserc.json`
* Add `release.yml` workflow in GitHub Actions
* Commit conventional commits to trigger **automated releases**
* Releases tab shows auto-generated release notes

---

## AWS Setup and Elastic Beanstalk Deployment

* Log into AWS console
* Create IAM user and generate access keys
* Add repository secrets for AWS credentials
* Create Elastic Beanstalk application and environment:

  * Node.js platform
  * Single-instance environment
  * Default VPC and public IP
  * EC2 instance profile and service role
* Configure optional settings for monitoring, rolling updates, logging, and platform options

---

## Deploy Workflow

* Create `deploy.yml` workflow triggered by **release event**
* Workflow steps:

  * Checkout code
  * Install dependencies
  * Run tests
  * Zip application
  * Configure AWS credentials
  * Deploy to Elastic Beanstalk using `einaregilsson/beanstalk-deploy`

---

## Release and Deployment Verification

* Create release on GitHub (`v1.3.0`)
* Trigger deployment workflow
* Deployment pipeline runs successfully
* Visit Elastic Beanstalk URL to confirm application is live

---

## Project Implementation
---
## Step 1: Create a GitHub Repository

Create a new repository named `github-actions-demo` and initialize it with a README.

![Step 1](./img/1.create_a_repository_named_github-actions-demo_and_initialized_it_with_README.png)

---

## Step 2: Copy Repository HTTPS URL

Copy the repository HTTPS URL to clone it locally.

![Step 2](./img/2.copy_the_repo_https_url.png)

---

## Step 3: Clone Repository Locally

Clone the repository using the copied link and navigate into it:

```bash
git clone <repo-https-url>
cd github-actions-demo
```

![Step 3](./img/3.git_clone_the_repo_using_the_copied_link_and_cd_into_it.png)

---

## Step 4: Verify Repository Contents

List files to verify that `README.md` exists:

```bash
ls
```

![Step 4](./img/4.ls_to_verify_README.md_should_show.png)

---

## Step 5: Initialize NPM

Initialize the project as a Node.js project:

```bash
npm init -y
```

![Step 5](./img/5.initialize_npm-y.png)

---

## Step 6: Verify `package.json`

Check that `package.json` now exists in the project folder:

![Step 6](./img/6.package-json_now_exist.png)

---

## Step 7: Install Express

Install Express framework as a dependency:

```bash
npm install express
```

![Step 7](./img/7.install_express.png)

---

## Step 8: Create `app.js` and Open in VS Code

Create the main application file `app.js` and open the project in VS Code:

```bash
touch app.js
code .
```

![Step 8](./img/8.touch_app-js_and_open_folder_in_vscode_using_code.png)

---

## Step 9: Add Code to `app.js`

Write the initial Node.js server code in `app.js`:

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => res.send('Hello World!'));

app.listen(port, () => console.log(`Server running on port ${port}`));
```

![Step 9](./img/9.add_code_to_app-js.png)

---

## Step 10: Install Mocha as Dev Dependency

Install Mocha for testing as a development dependency:

```bash
npm install --save-dev mocha
```

![Step 10](./img/10.npm_install_save_mocha_in_dev.png)

---

## Step 11: Create Test File

Create a test file named `test.js` inside the project:

```bash
touch test.js
```

![Step 11](./img/11.touch_test-js.png)

---

## Step 12: Write a Simple Test

Add a simple test in `test.js` to verify basic functionality:

```javascript
const assert = require('assert');

describe('Basic Test', () => {
  it('should return true', () => {
    assert.strictEqual(true, true);
  });
});
```

![Step 12](./img/12.write_simple_test_in_test-js.png)

---

## Step 13: Modify Scripts in `package.json`

Update the `scripts` section in `package.json` to include test and start commands:

```json
"scripts": {
  "test": "mocha",
  "start": "node app.js"
}
```

![Step 13](./img/13.modify_the_script_aspect_of_package-json.png)

---

## Step 14: Run Tests Locally

Run tests to ensure they pass:

```bash
npm test
```

![Step 14](./img/14.npm_test_to_test_locally_and_it_passed.png)

---

## Step 15: Run Application Locally

Start the application to test it in a local environment:

```bash
npm run start
```

![Step 15](./img/15.npm_run_to_run_application_locally.png)

---

## Step 16: Verify Application in Browser

Visit `http://localhost:3000` to check the running application. It should display:

```
Hello, World! This is version 1.0.0
```

![Step 16](./img/16.visited_localhost_3000_and_it_displays_Hello,%20World!_This_is_version_1.0.0.png)

---

## Step 17: Stop the Server

Press `Ctrl + C` in the terminal to stop the running server:

![Step 17](./img/17.ctrl_c_to_stop_running_server.png)

---

## Step 18: Create `.gitignore` File

Create a `.gitignore` file to exclude unnecessary files from Git:

```bash
touch .gitignore
```

![Step 18](./img/18.touch_gitignore.png)

---

## Step 19: Add `node_modules` to `.gitignore`

Prevent committing `node_modules` by adding it to `.gitignore`:

```
node_modules/
```

![Step 19](./img/19.add_node_modules_to_gitignore.png)

---

## Step 20: Commit and Push Changes

Commit all changes and push to the remote repository:

```bash
git add .
git commit -m "setup initial project structure, tests, and server"
git push origin main
```

![Step 20](./img/20.commit_and_push.png)

Perfect! Let’s continue the README with **steps 21–30**. I’ll maintain the same professional format and include all screenshots.

---

## Step 21: Verify Commit on GitHub

Check that your recent commit is now reflected on GitHub:

![Step 21](./img/21.commit_now_showing_on_github.png)

---

## Step 22: Create Workflow Directory

Create a `.github/workflows` directory in your project to store GitHub Actions workflows:

```bash
mkdir -p .github/workflows
```

![Step 22](./img/22.create_workflow_directory.png)

---

## Step 23: Create `ci.yml` Workflow File

Inside the workflows directory, create a `ci.yml` file for CI configuration:

```bash
touch .github/workflows/ci.yml
```

![Step 23](./img/23.create_ci-yml_in_workflows_directory.png)

---

## Step 24: Add Pipeline Script to `ci.yml`

Edit `ci.yml` to include the pipeline configuration, e.g., for testing Node.js application:

```yaml
name: Node.js CI
on:
  push:
    branches: [ main ]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm install
      - run: npm test
```

![Step 24](./img/24.add_pipeline_stript_to_ci-yml.png)

---
## Step 24b: Commit and Push Workflow File

Add, commit, and push the newly created workflow file to the repository:

```bash
git add .github/workflows/ci.yml
git commit -m "add CI workflow file"
git push origin main
```

![Step 24b](./img/24b.commit_and_push_workflow.png)

---

## Step 25: Create a Feature Branch

Create a new feature branch for updates:

```bash
git checkout -b feature/ci-test
```

![Step 25](./img/25.create_a_feature_branch.png)

---

## Step 26: Edit `app.js` and Send to Hello, World! CI Pipeline Active

Make edits in `app.js` and ensure that the CI pipeline is active and triggered:

![Step 26](./img/26.edit_res_send_to_Hello,_World!_CI_Pipeline_Active.png)

---

## Step 27: Commit and Push Feature Branch

Commit changes to the feature branch and push to GitHub:

```bash
git add .
git commit -m "update app.js for CI test"
git push origin feature/ci-test
```

![Step 27](./img/27.commit_and_push_to_created_branch.png)

---

## Step 28: Open Pull Request on GitHub

Go to GitHub, compare your feature branch to `main`, and ensure your changes are ready for a Pull Request:

![Step 28](./img/28.push_now_reflect_on_github_click_compare_and_pull_request.png)

---

## Step 29: Create Pull Request

Scroll down on GitHub and click **Create Pull Request** to merge the feature branch:

![Step 29](./img/29.scroll_down_to_compare_and_click_create_Pull_Request.png)

---

## Step 30: CI Pipeline Triggered

Once the Pull Request is created, the CI pipeline is automatically triggered and should pass:

![Step 30](./img/30.ci-pipeline_triggered_and_run_on_PR_and_passed.png)

---

Great! Let’s continue the README with **steps 31–40**, keeping it clean, professional, and consistent with the previous sections.

---

## Step 31: Merge Pull Request

Click **Merge Pull Request** on GitHub to merge your feature branch into `main`.

![Step 31](./img/31.click_merge_PR.png)

---

## Step 32: Confirm Merge

Confirm the merge to complete integrating the feature branch:

![Step 32](./img/32.confirm_merge.png)

---

## Step 33: Update Local Main Branch

Checkout to the `main` branch locally and pull the latest changes from GitHub:

```bash
git checkout main
git pull origin main
```

![Step 33](./img/33.checkout_to_main_and_pull_changes_from_github_to_main.png)

---

## Step 34: Install Semantic Release Dependencies

Install dependencies needed for automated semantic releases:

```bash
npm install --save-dev semantic-release @semantic-release/npm @semantic-release/github @semantic-release/commit-analyzer @semantic-release/release-notes-generator
```

![Step 34](./img/34.install_semantic-release_dependencies.png)

---

## Step 35: Create `.releaserc.json`

Create a `.releaserc.json` file in the root directory to configure semantic release:

```bash
touch .releaserc.json
```

![Step 35](./img/35.create_.releaserc.json_in_root_directory.png)

---

## Step 36: Add Code to `.releaserc.json`

Add the following configuration to `.releaserc.json`:

```json
{
  "branches": ["main"],
  "plugins": [
    "@semantic-release/commit-analyzer",
    "@semantic-release/release-notes-generator",
    "@semantic-release/npm",
    "@semantic-release/github"
  ]
}
```

![Step 36](./img/36.add_code_to_the_created_.releaserc.json_file.png)

---

## Step 37: Prevent Publishing to NPM

Add `"private": true` to `package.json` to prevent accidental publishing to NPM:

```json
"private": true
```

![Step 37](./img/37.add_private_true_to_package-json_to_prevent_publishing_to_npm.png)

---

## Step 38: Create `release.yml` Workflow

Create a new GitHub Actions workflow file `release.yml` in `.github/workflows`:

```bash
touch .github/workflows/release.yml
```

![Step 38](./img/38.create_release.yml_in_workflows.png)

---

## Step 39: Add Release Pipeline Script

Edit `release.yml` to include the semantic release deployment pipeline:

```yaml
name: Release Pipeline
on:
  push:
    branches:
      - main
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci
      - run: npx semantic-release
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```

![Step 39](./img/39.add_release_pipeline_script_release.yml_created.png)

---

## Step 39b: Configure GitHub Actions Permissions

Go to **Repository → Settings → Actions → General** and enable **Read & Write** permissions for workflows, and allow GitHub Actions to create and approve Pull Requests. Then save the settings.

![Step 39b](./img/39b.go_to_repo_action_general_setting_check_both_read_write_and_GA_create_and_approve_PR_then_save.png)

---

## Step 40: Commit Conventional Commit and Push

Commit all changes using a conventional commit message and push to GitHub:

```bash
git add .
git commit -m "chore: configure semantic release"
git push origin main
```

![Step 40](./img/40.commit-conventional-commit_and_push.png)

---

Perfect! Let’s continue the README with **steps 41–50**, keeping the professional style and linking each screenshot.

---

## Step 41: Edit `app.js` to Trigger Pipeline

Make the necessary edits in `app.js` that will trigger the release pipeline upon commit:

![Step 41](./img/41.edit_app.js_to_trigger_pipeline.png)

---

## Step 42: Commit and Push Changes

Commit your edits and push them to GitHub:

```bash
git add .
git commit -m "fix: trigger pipeline for testing release"
git push origin main
```

![Step 42](./img/42.add_commit_and_push.png)

---

## Step 43: Verify Workflow Run

Go to the **Actions** tab in GitHub to ensure the workflow run completed successfully with no errors:

![Step 43](./img/43.checked_action_tab_workflow_run_successfully_with_no_error.png)

---

## Step 44: Access Release Pipeline

Click on the **Release Pipeline** to view the detailed run:

![Step 44](./img/44.click_release_pipeline.png)

---

## Step 45: Release Pipeline Completed

Check that the release pipeline has run completely and all steps succeeded:

![Step 45](./img/45.release_pipeline_run_completely.png)

---

## Step 46: Verify Release Version on GitHub

On the repository dashboard, the new release version now displays:

![Step 46](./img/46.on_the_repo_dashboard_release_version_now_displays.png)

---

## Step 47: View Release Details

Clicking on the release version shows the release notes and details of the fixes included:

![Step 47](./img/47.clicking_it_shows_fix_details.png)

---

## Step 48: Receive Email Notification

If configured, receive an email notification about the new bug fixes and release:

![Step 48](./img/48.received_email_on_the_new_bug_fixes_as_well.png)

---

## Step 49: Log into AWS Console

Log into the AWS Management Console and navigate to **IAM** to manage users and permissions:

![Step 49](./img/49.log_into_aws_console_and_search_IAM_then_click_on_it.png)

---

## Step 50: Access Users in IAM

Click on **Users** in the IAM dashboard to see the list of IAM users:

![Step 50](./img/50.click_on_users.png)

---

## Step 51: Verify or Create Active Access Key

Ensure the IAM user has an **active access key**. If not, create one. Note the displayed key for use in GitHub Secrets:

![Step 51](./img/51.the_user_has_active_access_key_create_if_yours_dont_note_the_displayed_key.png)

---

## Step 52: Copy AWS Credentials

On your local machine, view your AWS credentials and copy the **Access Key ID** and **Secret Access Key**:

```bash
cat ~/.aws/credentials
```

![Step 52](./img/52.cat_.aws_credentials_copy_access_key_on_the_aws_users_account_and_its_secret_key.png)

---

## Step 53: Open GitHub Secrets

Go to your repository on GitHub, click **Settings → Secrets and variables → Actions**:

![Step 53](./img/53.on_the_repo_click_settings_then_secrets_and_variable_then_actions.png)

---

## Step 54: Add New Repository Secret

Click **New repository secret** to add AWS credentials:

![Step 54](./img/54.click_new_repository_secret.png)

---

## Step 55: Add `AWS_ACCESS_KEY_ID`

Paste `AWS_ACCESS_KEY_ID` as the **name** and the Access Key ID as the **secret value**, then click **Add secret**:

![Step 55](./img/55.paste_AWS_ACCESS_KEY_ID_in_name_and_the_ID_in_secret_then_add_secret.png)

---

## Step 56: Add `AWS_SECRET_ACCESS_KEY`

Similarly, add `AWS_SECRET_ACCESS_KEY` with its value and save as a secret:

![Step 56](./img/56.also_add_AWS_SECRET_ACCESS_KEY_and_its_secret.png)

---

## Step 57: Add `AWS_REGION`

Finally, add `AWS_REGION` as a secret with the appropriate AWS region value (e.g., `us-east-1`):

![Step 57](./img/57.finally_add_AWS_REGION_and_add_secret.png)

---

## Step 58: Open Elastic Beanstalk Console

In the AWS Console, search for **Elastic Beanstalk** and click on it to start deploying your application:

![Step 58](./img/58.on_aws_console_search_for_Elastic_Beanstalk_and_click_on_it.png)

---

## Step 59: Create a New Application

Click **Create Application** to begin setting up a new Elastic Beanstalk application:

![Step 59](./img/59.click_create_application.png)

---

## Step 60: Select Web Server Environment

Select **Web Server Environment**, enter your **application name**, and scroll down to configure the environment:

![Step 60](./img/60.select_webserver_environment_name_application_and_scroll_down.png)

---

Great! Let’s continue the README with **steps 61–70**, keeping the same clear and professional style.

---

## Step 61: Select Node.js Platform and Upload Code

Choose the **Node.js platform version 20**, select **Upload code from S3**, and add a deployment label (e.g., `v1.0.0`):

![Step 61](./img/61.select_nodejs_platform_version_20_select_upload_code_s3_add_deployment_label_v1.0.0_.png)

---

## Step 62: Click Next

Click **Next** to proceed to the next configuration step:

![Step 62](./img/62.click_next.png)

---

## Step 63: Configure Service Access

In the **Configure service access** step, click **Create Service Role**:

![Step 63](./img/63.now_in_Configure_service_accessclick_create_Service_role_.png)

---

## Step 64: Set Use Case to Elastic Beanstalk

Ensure the **use case** is set to **Elastic Beanstalk**, then click **Next**:

![Step 64](./img/64.ensure_usecase_is_set_to_ElasticBeanStalk_click_next.png)

---

## Step 65: Create Service Role with Appropriate Permissions

Review the permissions and click **Next → Review → Create** to create the service role:

![Step 65](./img/65.appropraite_permission_created_click_next_review_and_create.png)

---

## Step 66: Switch Back to Elastic Beanstalk Creation

Once the role is created, switch back to the **Elastic Beanstalk application creation** tab:

![Step 66](./img/66.role_created_switch_back_to_EBS_creation_tab.png)

---

## Step 67: Create EC2 Instance Profile Role

Select **aws-elasticbeanstalk-service-role** and click to **create an EC2 instance profile role**:

![Step 67](./img/67.select_aws-elasticbeanstalk-service-role_click_to_create_EC2_profile_role.png)

---
## Step 68: Ensure Elastic Beanstalk Compute is Selected

Ensure **Elastic Beanstalk compute** is selected, then click **Next**:

![Step 68](./img/68.ensure_EBS-compute_selected_then_next.png)

---
## Step 68b: Review EC2 Instance Profile Role

Ensure the appropriate permissions are selected, review, and click **Create Role**:

![Step 68b](./img/68b.appropraite_permission_selected_click_next_review_and_create_role.png)

---

## Step 69: Assign Roles and Key Pair

Select the created **service role**, click **Refresh** if the role is missing, then select the **EC2 key pair**, and click **Next**:

![Step 69](./img/69.select_created_role_click_refresh_button_if_role_is_missing_then_select_and_select_key_pair_then_next.png)

---

## Step 70: Configure VPC and Subnets

Select the **default VPC** and its subnets, and enable **public IP**:

![Step 70](./img/70.select_default_vpc_and_its_subnets_enable_public_ip.png)

---

## Step 71: Add Project and Environment Tags

Add **Project** and **Environment** tags for your Elastic Beanstalk environment, then click **Next**:

![Step 71](./img/71.add_Project_and_Environment_tags_and_click_next.png)

---

## Step 72: Configure Root Volume and EC2 Settings

Leave the **root volume** at default, enable **only IMDSv1**, set CloudWatch monitoring interval to **5 minutes**, and select the **default EC2 security group**:

![Step 72](./img/72.leave_root_volume_at_default_enable_only_IMDSv1_ACW_5mins_select_default_EC2_SG.png)

---

## Step 73: Set Instance Type and Scaling

Choose **Single instance**, **On-Demand**, architecture **x86_64**, instance type **t3.micro**, and click **Next**:

![Step 73](./img/73.set_single_instance_on-demand_x86_64_t3micro_and_click_next.png)

---

## Step 74: Configure Monitoring

Set **enhanced health monitoring**, CloudWatch metrics, and other monitoring options according to your requirements:

![Step 74](./img/74.set_monitoring_section.png)

---

## Step 75: Enable Managed Platform Updates

Enable **managed platform updates**, select the weekly maintenance window, and choose **minor and patch updates**:

![Step 75](./img/75.set_managed_platform_update.png)

---

## Step 75b: Configure Rolling Updates and Deployment

Set rolling update policies and deployment preferences to control how instances are updated:

![Step 75b](./img/75b.set_rolling_update_deployment.png)

---

## Step 76: Configure Platform Software Options

Set platform-specific options such as **proxy server**, **X-Ray**, **S3 log storage**, and **instance log streaming**:

![Step 76](./img/76.set_platform_software_option.png)

---

## Step 77: Click Next

After reviewing optional settings, click **Next** to proceed to the final step:

![Step 77](./img/77.click_next.png)

---

## Step 78: Review Configuration and Create Environment

Review all settings, verify that everything is correct, and click **Create**:

![Step 78](./img/78.review_and_click_create.png)

---

## Step 79: Environment Creation in Progress

The Elastic Beanstalk environment is being created:

![Step 79](./img/79.elastic_bean_environment_creating.png)

---

## Step 80: Environment Successfully Launched

Once the environment launches successfully, copy the provided **Elastic Beanstalk domain** and open it in a new browser tab to verify deployment:

![Step 80](./img/80.ebs_environment_launch_successfully_copy_the_domain_and_visit_in_a_new_tab.png)

---

## Step 81: Welcome to Elastic Beanstalk Page

Visit your Elastic Beanstalk environment’s domain to verify the application is running successfully:

![Step 81](./img/81.welcome_to_ebs_page_showing.png)

---

## Step 82: Add Deployment Workflow

Create a **deployment workflow** in `.github/workflows` for deploying the application to Elastic Beanstalk:

![Step 82](./img/82.add_deployment_workflow.png)

---

## Step 83: Configure `deploy.yml` File

Edit the `deploy.yml` workflow file with the steps to **checkout code, install dependencies, run tests, zip the application, configure AWS credentials, and deploy to Elastic Beanstalk**:

![Step 83](./img/83.configure_deploy.yml_file.png)

---

## Step 84: Commit and Push Deployment Workflow

After creating the deployment workflow file, **commit and push** it to your repository:

![Step 84](./img/84.commit_and_push_deployment_workflow.png)

---

## Step 85: Edit `app.js` to Trigger Deployment Workflow

Make a small **change in `app.js`** to trigger the deployment workflow when pushed:

![Step 85](./img/85.edit_app.js_to_trigger_deploy_workflow.png)

---

## Step 86: Commit and Push Changes

Commit and push the changes to the repository to trigger the deployment workflow:

![Step 86](./img/86.commit_and_push_changes.png)

---

## Step 87: Navigate to Repository Actions

Go to the **Actions tab** in your GitHub repository and click on the **Deploy to Elastic Beanstalk workflow**:

![Step 87](./img/87.navigate_to_repo_actions_and_click_deploy_to_EBS_workflow.png)

---

## Step 88: Workflow Has Not Run Yet

Since the workflow is newly configured, it will show **“This workflow has no runs yet”**:

![Step 88](./img/88.workflow_has_not_run_yet.png)

---

## Step 89: Update `deploy.yml` with Write Permission

Edit the `deploy.yml` to ensure the workflow has **write permission to push deployment tags or trigger further actions**:

![Step 89](./img/89.update_deploy.yml_with_write_permission.png)

---

## Step 90: Push and Commit Changes

Push and commit the changes to GitHub to activate the workflow:

![Step 90](./img/90.push_and_commt_changes.png)

---

## Step 91: Navigate to Repository Releases

Go to your GitHub repository **Releases tab** to view existing releases:

![Step 91](./img/91.navigate_to_repo_page_and_click_on_releases.png)

---

## Step 92: New Release Appears

The newly created release is visible, showing the **version number and commit**:

![Step 92](./img/92.new_release_shows.png)

---

## Step 93: Workflow Did Not Run

At this point, the deployment workflow did **not run automatically**, indicating a configuration mismatch:

![Step 93](./img/93.however_workflow_did_not_run.png)

---

## Step 94: Update `deploy.yml` for Release Pipeline

Edit the `deploy.yml` workflow to **match the release pipeline name** and ensure **unique version labels** for Elastic Beanstalk deployments:

![Step 94](./img/94.update_deploy.yml_to_match_release_pipeline_name_and_unique_label_for_ebs.png)

---

## Step 95: Commit and Push Changes

Commit and push the updated workflow to GitHub:

![Step 95](./img/95.commit_and_push_changes.png)

---

## Step 96: Make a New Feature Commit

Create a **new feature commit** to trigger the deployment pipeline and push it to the repository:

![Step 96](./img/96.make_new_feat_commit_to_trigger_pipeline_and_push.png)

---

## Step 97: Release Version v1.3.0

Create a new release on GitHub to version the application as **v1.3.0**:

![Step 97](./img/97.release_now_v1.3.0.png)

---

## Step 98: Deploy to AWS Elastic Beanstalk Pipeline Runs Successfully

The **Deploy to EBS workflow** now runs successfully, deploying the latest application version:

![Step 98](./img/98.deploy_to_aws_ebs_pipeline_now_run_successfully.png)

---

## Step 99: Application Live on Elastic Beanstalk

Finally, visit the **Elastic Beanstalk URL** to confirm the application is **live and accessible**:

![Step 99](./img/99.application_now_live_on_the_ebs_link.png)

---




## CI/CD Workflow Summary

1. **CI pipeline**: Runs tests on every PR or push.
2. **Semantic release pipeline**: Automatically generates release notes and versions using conventional commits.
3. **Deploy to Elastic Beanstalk**: Triggered on release, builds zip, uploads to S3, deploys to EBS.

---

## References

* [GitHub Actions Documentation](https://docs.github.com/en/actions)
* [AWS Elastic Beanstalk Documentation](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html)
* [Semantic Release](https://semantic-release.gitbook.io/semantic-release/)
* [einaregilsson/beanstalk-deploy](https://github.com/einaregilsson/beanstalk-deploy)



