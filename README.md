# cloud-formation-templates
Cloud Formation Templates for deploying Server less Applications

## build-pipeline.yaml
The template `build-pipeline.yaml` can be used to deploy code from GitHub to AWS CodePipeline. 
The pipeline has threee stages namely Source, Build and Deploy
1. In Source, the code is fetched from GitHub upon a commit to master branch (can be switched to any other branch)
2. In build, the dependencies will be built based on the instructions in buildspec.yaml in the respective repository. You may customize this step to have other functionalities too. Such as running unit tests, linter etc
3. In Deploy, the code is deployed using CloudFormation. This step creates a stack in which all the resources and roles mentioned in the `template.yaml` of the repository are created.

Prior to creating pipeline, you have to create a GitHub Access Token for the following field
`OAuthToken: "{{resolve:ssm:/github/personal_access_token:1}}"`
To generate this token, Go to your GitHub Settings -> Developer Settings -> Personal Access Tokens -> Generate new token

In my case, I kept this token in my SSM Parameter store since this is sensitive information.

Uploading `build-pipeline.yaml` with some parameter entries is the only manual step needed to deploy a service.  

Make sure that the user who uploads the templates in Cloud Formation has access to read from SSM Parameter store

Later on, upon each commit to master (or any other if you configure it that way) branch of the repository which uses this pipeline, the deployment process is automated in a CI/CD way.