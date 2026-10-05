# Quote of the Day API - CI/CD pipeline

**NOTE** This assignment is done using the public repository due to Render.com restrictions.

In this assignment, you will:
- Work with a pre-built Node.js API that returns random motivational quotes.
- Fix linting errors and make all tests pass.
- Set up **two** GitHub Actions workflows:
   - **CI Workflow** — Runs on every push and pull request to check code quality.
   - **Deployment Workflow** — Runs only when you create a GitHub Release and deploys to Render via webhook.

# Steps to Complete:

## Part 1 - CI workflow (1 point)
1. Clone repository locally
3. Install Dependencies
4. Fix Linting Issues
```
npm run lint
```
5. Fix Failing Tests
```
npm test
```
6. Create `.github/workflows/ci-cd.yml`
This workflow runs on every push and pull request. It should run linter and tests

Goal: Every code change is checked automatically.

## Part 2 — CD job (2 points)
7. Render Deploy Hook
- Go to Render and sign in.
- Create a New Web Service.
- Connect your GitHub account and select your repo.
- Copy the Deploy Hook URL.

8. Add the Deploy Hook as a GitHub Secret 
```
Name: RENDER_DEPLOY_HOOK
Value: (paste your Deploy Hook URL)
```
9. Add a new Job that deploys app to the Render using web hook.
- Job is run when new code is pushed to main branch.
- Job is executed only after CI workflow is run successfully.

Verify Deployment

Visit your Render URL → `/quote` endpoint should return a random quote.

To confirm that your workflow is functioning correctly, try modifying the source code. For instance, you could update the response in `app.js` to include extra text.

Commit and push your changes to the GitHub repository. Once the Render deployment is complete, check your application to ensure the response reflects your update.

## Part 3 - Release deployment (2 points)
Goal: Code is deployed only when GitHub release is published.

10. Move deployment to own workflow file `cd.yml`.
- This workflow runs when new release is published.

11. Create Github Release
Go to Releases → Create a new release.
Tag version (e.g., v1.0.0).

Publish release — the deployment workflow will run and triggers Render deployment.
