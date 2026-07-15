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

## Related Repository:
- [Demo Project](https://github.com/felix-karg/java-maven-app) (Branch `module_8.15-webhooks`)

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
17. Now we need to configure the hook in the GitHub [demo repository](https://github.com/felix-karg/java-maven-app)
18. In repository settings go to 'Webhooks' and click 'Add webhook'
19. Set `http://<jenkins-url>:8080/github-webhook/` (the endpoint with trailing slash is important!)
20. Disable SSL verification (we use unsecure connection with our Jenkins)
21. Save and push a change to see if all works as expected
22. If pipeline does not trigger, make sure it ran at least once successfull manually and try to push again.
23. For multibranch pipelines another plugnin is necessary: 'Multibranch Scan Webhook Trigger'. So install it.
24. After installation in configuration of multibranch pipeline under 'Scan Multibranch Pipeline Triggers'
    there is a new option 'Scan by webhook' available.
25. Choose that option and type any name into 'Trigger token' test field
26. Click on the `?` next to 'Trigger token' and copy the URL shown in the tool tip
27. Go to settings of GitHub repository and create another webhook
28. Paste the URL from step 26 into 'URL' field
29. Replace 'JENKINS_URL' by your actual Jenkins URL and '[Trigger token]' by the token name from step 25
30. Again disable SSL authentication and save
31. Make a change in code and push again to see if multibranch pipeline is triggered as expected
