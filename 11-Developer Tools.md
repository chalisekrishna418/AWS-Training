# Developer Tools

## CodeCommit
- It is a version control service hosted by AWS that you can use to privately store and manage assets in the cloud.
- You can host documents, source code, and binary files in CodeCommit.
- You can migrate to CodeCommit from any Git-based repository.
- You can integrate CodeCommit with CodeBuild, CodeDeploy and other AWS services for CI/CD purposes.

## CodeBuild
- It is a fully managed build service in the cloud.
- CodeBuild compiles your source code, runs unit tests, and produces artifacts that are ready to deploy.
- CodeBuild Charges for number of build minutes required for the build to run.
- Codebuild builds the code based on a specification called build-spec. You can define your own spec file or use the existing ones.
- You can also integrate CodeBuild with CodeCommit, CodeDeploy and other AWS services for CI/CD usecases.

## CodeDeploy
- It is a deployment service that enables us to automatically deploy applications.
- Using Codedeploy you can deploy to Amazon EC2 instances, on-premises instances, serverless Lambda functions, or Amazon ECS services.
- You can deploy Code, Lambda functions, Serverless AWS Lambda functions, Web and configuration files, Executables, Packages, Scripts, Multimedia files, Docker Images.
- It deploys application content that runs on a server and is stored in Amazon S3 buckets, CodeCommit, GitHub repositories, or Bitbucket repositories without making any change to the repositories.
- You can automatically or manually stop and roll back deployments if there are errors.
- You can use several deployments like Blue/Green, Rollout, Canary deployments and you can always rollback your deployment if there are errors.

## Cloud9
- Cloud9 is a AWS Service that offers cloud IDE.
- It offers rich code-editing experience with support for several programming languages and runtime debuggers, as well as a built-in terminal.
- AWS Cloud9 acheives this by provisioning an EC2 instance, setting up your environment over there.
- With AWS Cloud9, you can code, build, run, test, debug, and release software.
- You can also collaborate easily on a piece of code among developers.
- You can work with other AWS services from the Cloud9 provided terminal. This would require you to have the necessary permissions provided to Cloud9 using IAM Roles. 

## CodePipeline
- It is a continuous delivery service that you can use to model, visualize, and automate the steps required to release your software.
![Screen Shot 2022-06-16 at 06.43.02.png](:/cd8b2d9ad9e0418092832efaadf483a1)
- You can integrate CodeCommit, CodeBuild and Codebuild along with multiple services to build a pipeline

## Reading Materials
- [AWSDocs - CodeCommit](https://docs.aws.amazon.com/codecommit/latest/userguide/welcome.html)
- [AWSDocs - CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html)
- [AWSDocs - Cloud9]()
- [Medium Blog - What is Cloud9 ](https://medium.com/@madhucynixit/what-is-aws-cloud9-6d83c3c4e9f4)
