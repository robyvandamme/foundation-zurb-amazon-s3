# ZURB Foundation Amazon S3
Extended [ZURB Foundation for Sites template](https://github.com/zurb/foundation-zurb-template) to enable automated builds and deployments to [Amazon S3](https://aws.amazon.com/websites/) using [Wercker](http://wercker.com).

[![wercker status](https://app.wercker.com/status/4cf6da247317b86af647afbc7e9acddc/m "wercker status")](https://app.wercker.com/project/bykey/4cf6da247317b86af647afbc7e9acddc)

Live website: [http://foundation-zurb-amazon-s3.s3-website-ap-northeast-1.amazonaws.com/](Check the deployed website on S3)

## Prerequisites
- An [AWS account (Free)](https://aws.amazon.com/free/)
- A [Werker account (Free)](http://wercker.com)

## Getting started
- Clone the repository to your machine
- Create a website on Amazon S3 using the s3-website.template using the AWS CLI
```aws cloudformation create-stack --stack-name YOUR-STACK-NAME --template-body file:////YOUR-LOCAL-PATH/zurb-foundation-amazon-s3/s3-website.template --parameters ParameterKey=BucketName,ParameterValue=YOUR-BUCKET-NAME ```


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
