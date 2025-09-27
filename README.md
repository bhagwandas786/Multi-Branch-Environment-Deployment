"Multi-Branch Environment Deployment"

* This project implements a multi-branch CI/CD pipeline using GitHub Actions.
* CI Job → Runs linting & tests on all PRs and pushes, uploads test results as artifacts.
* QA Deployment → Triggered on dev branch pushes, downloads artifacts and simulates deployment to QA.
* Production Deployment → Triggered on main branch pushes, downloads artifacts and deploys to Production.
* Slack Notification → Sends a success message after Production deployment.
✅ Ensures code quality overall,
✅ Prevents overlapping deploys with concurrency,
✅ Provides automated deployments for QA & Production,
✅ Notifies the team via Slack after Production success.

Branch to Environment Mapping
| Branch / Event | Environment  | Deploy? | Notes                  |
|----------------|--------------|---------|------------------------|
| `main` (push)  | Production   | ✅      | Live environment       |
| `dev` (push)   | QA           | ✅      | Test / QA environment  |
| PR (any)       | None         | ❌      | Runs CI only           |


FEATURES
- Multi-branch deployment (`dev → QA`, `main → Production`)
- Artifacts passed between jobs
- Concurrency control (no overlapping deploys)
- Slack notifications on Production success

HOW TO USE?
1. Clone the repo:  
   git clone <your-repo-url>
2. Create dev and main branches
3. Push to dev → Deploys to QA
4. Push to main → Deploys to Production
5. Configure Slack Webhook in repository secrets:
SLACK_WEBHOOK_URL

FLOW OF GITHUB ACTIONS WITH CICD AUTOMATION:

- CI Job for Pull Requests
This diagram shows that whenever a pull request is made, it automatically triggers a CI (Continuous Integration) job. This job's purpose is to run linting (code style checks) and tests to ensure the new code is clean and doesn't break anything. The job will either succeed (green checkmark) or fail (red 'X'). No deployment happens at this stage.
<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/6ccfba28-2460-4ae2-9737-11c8759bcdb3" />

- QA Deployment
This diagram illustrates that a push (or merge) to the dev branch will trigger a deployment to the QA (Quality Assurance) environment. This allows your team to test the new features in a dedicated testing environment before they go live.
<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/1b59dfe4-feae-462f-9220-f9763cd8f2a6" />

- Production Deployment
This diagram shows that a push (or merge) to the main branch triggers a deployment to the Production environment. This is the final step, making the new code live for all users.
<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/4b50ff7e-b3cf-4ce9-975e-6ae00dd76154" />

- Production Deployment with Slack Notification
This diagram adds the extra challenge step: after a successful deployment to the Production environment, a final action is triggered to send a notification to Slack. This keeps the team informed about successful deployments.
<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/d4c415c2-86bb-4581-b34f-aec089ceb0b4" />

RESULTS FOR ACTIONS:
1. FOR CI ACTION: https://github.com/bhagwandas786/Multi-Branch-Environment-Deployment/actions/runs/17842776956
2. FOR QA DELPOYMENT ACTION: https://github.com/bhagwandas786/Multi-Branch-Environment-Deployment/actions/runs/17847352070
3. FOR PROD DEPLOYMENT ACTION: https://github.com/bhagwandas786/Multi-Branch-Environment-Deployment/actions/runs/17847519035





