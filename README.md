
# Creating Microsoft Azure Pipelines

This guide explains how to create and configure Microsoft Azure Pipelines for automating your build, test, and deployment processes in Azure DevOps.

## What is Azure Pipelines?

Azure Pipelines is a cloud service that supports continuous integration (CI) and continuous delivery (CD) to build, test, and deploy your code automatically. It supports many languages, platforms, and cloud services.

---

## Prerequisites

- An **Azure DevOps** account (you can sign up for free [here](https://azure.microsoft.com/en-us/services/devops/))
- A project repository in Azure Repos, GitHub, or other supported version control system
- Basic knowledge of YAML (for pipeline definitions) or classic editor familiarity

---

## Steps to Create an Azure Pipeline

### 1. Navigate to Azure DevOps

- Sign in to your Azure DevOps organization.
- Select your project or create a new one.

### 2. Go to Pipelines

- From the left menu, click **Pipelines**.
- Click on **Create Pipeline**.

### 3. Connect Your Repository

- Choose your repository source (e.g., Azure Repos Git, GitHub, Bitbucket).
- Authorize access if needed.

### 4. Configure Your Pipeline

- Select to use the **YAML** pipeline or the **classic editor**.
- For YAML, you can either use the starter pipeline or define your own `azure-pipelines.yml` file.

Example minimal `azure-pipelines.yml`:

```yaml
trigger:
- main

pool:
  vmImage: 'ubuntu-latest'

steps:
- task: UseNode@2
  inputs:
    version: '14.x'
- script: npm install
  displayName: 'Install dependencies'
- script: npm run build
  displayName: 'Build project'
- script: npm test
  displayName: 'Run tests'
```

### 5. Run Your Pipeline

- Save and run your pipeline.
- Monitor the build process in real-time via the Azure DevOps UI.

### 6. Set up Continuous Deployment (Optional)

- Add release pipelines to deploy artifacts to environments like Azure App Service, Kubernetes, VMs, etc.

---

## Tips & Best Practices

- Use YAML pipelines for versioning your pipeline as code.
- Use pipeline variables to manage environment-specific settings.
- Set up pipeline triggers for automatic runs on code commits or pull requests.
- Secure secrets using Azure Key Vault or pipeline secrets.

---

## Useful Links

- [Azure Pipelines Documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/?view=azure-devops)
- [YAML Schema Reference](https://docs.microsoft.com/en-us/azure/devops/pipelines/yaml-schema)
- [Classic Pipeline Editor](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/classic-editor)

---

## License

This project is licensed under the MIT License.
