# Module 8.15 of DevOps Bootcamp by [TechWorld with Nana](https://www.techworld-with-nana.com/)
Configure Webhook to trigger CI Pipeline automatically on every change

## Technologies used:
- Jenkins
- GitHub
- Git
- Docker
- Java
- Maven

## Project Description:
- Install GitHub Plugin in Jenkins
- Configure GitHub access token and connection to Jenkins in GitHub project settings
- Configure Jenkins to trigger the CI pipeline whenever a change is pushed to GitHub

## Implementation Steps:
1. Check if GitHub Plugin in Jenkins is already installed at 'Manage Jenkins' -> 'Plugins' -> 'Installed Plugins'
2. If not, install the Plugin at 'Available Plugins'
3. When the plugnin is installed, at 'Manage Jenkins' -> 'System' there is a GitHub configuration available
4. In this GitHub configuration click 'Add GitHub Server'
5. Give a name (e.g. 'github-conn') and let 'API-URL' as it is (`https://api.github.com`)
6. In GitHub go to 'Settings' -> 'Developer Settings'
7. Click 'Personal access token' -> 'Tokens (classic)'
8. Click 'Generate new token' -> 'Generate new token (classic)'
9. Give a name
10. Chosse scopes `repo` and `admin:repo_hook` and click 'Generate token'
11. Copy token before you close the window (it will never be accessible again)!
12. Back in Jenkins go to 'Manage Jenkins' -> Credentials
13. Choose global scope and click 'Add credentials'
14. Choose 'Secret text' as credential type, paste the token to the 'Secret' field, give a name (ID) and click 'Create'
15. Back to 'Manage Jenkins' -> 'System' -> 'GitHub' -> 'GitHub Servers' and choose newly created secret
16. Click 'Test connection' to verify that all works as expected
17. 
