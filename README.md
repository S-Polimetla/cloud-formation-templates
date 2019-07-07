# cloud-formation-templates
Cloud Formation Templates for deploying Server less Applications

The template `build-pipeline.yaml` can be used to deploy code from GitHub to AWS CodePipeline. 
The pipeline has threee stages namely Source, Build and Deploy
1. In Source, the code is fetched from GitHub upon a commit to master branch (can be switched to any other branch)
2. In build, the dependencies will be built based on the instructions in buildspec.yaml in the respective repository. You may customize this step to have other functionalities too. Such as running unit tests, linter etc
3. In Deploy, the code is deployed using CloudFormation. This step creates a stack in which all the resources and roles mentioned in the template.yaml of the repository are created.

Uploading `build-pipeline.yaml` with some parameter entries is the only manual step needed to deploy a service. 