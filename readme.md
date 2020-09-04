# ZURB Foundation Amazon S3
Extended [ZURB Foundation for Sites template](https://github.com/zurb/foundation-zurb-template) to enable automated builds and deployments to [Amazon S3](https://aws.amazon.com/websites/) using [Wercker](http://wercker.com).

## Prerequisites
- An [AWS account (Free)](https://aws.amazon.com/free/)
- A [Wercker account (Free)](http://wercker.com)

## Additions
- wercker.yml: configuration for Wercker.
- s3-website.template: example CloudFormation template to create a stack for the S3 website.
- s3-sync.policy: example IAM policy to allow syncing to S3.

## Getting started
1. (Wercker) Create a new build on [Wercker](http://wercker.com) and point it to your repository on GitHub.
2. (Wercker) Trigger a build.
3. (AWS) Create a website on Amazon S3 using the s3-website.template in the root of the repository. Example using the CLI (replace the YOUR-STACK-NAME, YOUR-LOCAL-PATH and YOUR-BUCKET-NAME with the relevant values):
```aws cloudformation create-stack --stack-name YOUR-STACK-NAME --template-body file:////YOUR-LOCAL-PATH/zurb-foundation-amazon-s3/s3-website.template --parameters ParameterKey=BucketName,ParameterValue=YOUR-BUCKET-NAME ```
3. (AWS) Create a new IAM user to allow Wercker to sync to Amazon S3. You will need to add the user’s Access Key ID and Secret Access Key as environment variables in your deploy configuration later on.
4. (AWS) Create an IAM policy that allows syncing your website to S3 (example s3-sync.policy in the root of the repository) and attach the policy to the user you created in the previous step.
6. (Wercker) Create a Deploy for your build. You will need to specify the following variables (declared in the wercker.yml in the root of the repository)
		- ~AWS_ACCESS_KEY_ID~ (of the IAM user you created in step 3)
		- ~AWS_SECRET_KEY~ (of the IAM user you created in step 3)
		- ~BUCKET~ (you website bucket ‘s3://your-bucket-name')
7. (Wercker) Trigger a Deploy 

## ZURB Template

[![devDependency Status](https://david-dm.org/zurb/foundation-zurb-template/dev-status.svg)](https://david-dm.org/zurb/foundation-zurb-template#info=devDependencies)

**Please open all issues with this template on the main [Foundation for Sites](https://github.com/zurb/foundation-sites/issues) repo.**

This is the official ZURB Template for use with [Foundation for Sites](http://foundation.zurb.com/sites). We use this template at ZURB to deliver static code to our clients. It has a Gulp-powered build system with these features:

- Handlebars HTML templates with Panini
- Sass compilation and prefixing
- JavaScript concatenation
- Built-in BrowserSync server
- For production builds:
  - CSS compression
  - JavaScript compression
  - Image compression

## Installation

To use this template, your computer needs:

- [NodeJS](https://nodejs.org/en/) (0.12 or greater)
- [Git](https://git-scm.com/)

This template can be installed with the Foundation CLI, or downloaded and set up manually.

### Using the CLI

Install the Foundation CLI with this command:

```bash
npm install foundation-cli --global
```

Use this command to set up a blank Foundation for Sites project with this template:

```bash
foundation new --framework sites --template zurb
```

The CLI will prompt you to give your project a name. The template will be downloaded into a folder with this name.

### Manual Setup

To manually set up the template, first download it with Git:

```bash
git clone https://github.com/zurb/foundation-zurb-template projectname
```

Then open the folder in your command line, and install the needed dependencies:

```bash
cd projectname
npm install
bower install
```

Finally, run `npm start` to run Gulp. Your finished site will be created in a folder called `dist`, viewable at this URL:

```
http://localhost:8000
```

To create compressed, production-ready assets, run `npm run build`.
