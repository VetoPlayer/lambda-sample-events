# Lambda Sample Events

This repository contains a community curated collection of sample AWS Lambda events generated by various AWS services. This can come in handy to unit test a Lambda function that is triggered by another AWS service. To keep the content machine parsable, there is a JSON file that defines the mapping between the event file names and descriptions, canonical identifier and [mustache](https://mustache.github.io/) tag names available to customize the event.

## How to use

There are many ways of using the events: (We are still working on streamlining the UX. See Roadmap section if you want to help)

**Prerequesite:** Clone the repo `git clone https://github.com/sanathkr/lambda-sample-events`

### SAM Local CLI

SAM Local CLI allows you to run Lambda functions locally. You can invoke Lambda function

- Download the [SAM Local CLI](https://github.com/awslabs/aws-sam-local)
- Use `sam local invoke -e <path-to-event-json>`

### AWS CLI

To invoke AWS Lambda function on cloud by passing the event,

`aws lambda invoke --function-name <functionname> --payload file:///path/to/event.json output.txt`

## Conventions

**Folder Structure**: Sample events are available as JSON files under the [events](events/) folder. Each folder here is named after the AWS CLI command name used by the service. Ex: AWS CloudWatch Logs event is location under [/logs](events/logs) folder. AWS CloudTrail events is located under [/cloudtrail](events/cloudtrail) folder.

**event-mapping.json**: This file contains the mapping between each event file with their descriptions, identifier and mustache tag names available to customize the event. This file can be used by IDEs and CLIs to display relevant help text about each event.

**tags-mapping.json**: There are some tags that are general across all events such as AWS Region or AWS AccountId. This file defines the common tag names along with
usage instructions and default value. Tags used in the `events-mapping.json` file can refer to the tags defined here using the tag's name to inherit default values
and usage instructions.

## Roadmap - Help needed!

This repository is a work in progress. Here is a prioritized list of things we are working on now. Follow each Github Milestones & Github Issues for progress and feel free to send us a pull request if you'd like to contribute. The list here is just a general direction. We might re-prioritize as we hear feedback from community

### v0.1.0 Milestone:

Once the repository reaches good maturity and a stable community of contributors, we hope to integrate this with local development tools like [AWS SAM Local CLI](https://github.com/awslabs/aws-sam-local).

Follow https://github.com/sanathkr/lambda-sample-events/milestone/1

### v0.2.0 Milestone

- [ ] Build libraries to render mustache and generate JSON for an event:
    - [ ] Javascript
    - [ ] Python
    - [ ] Go (https://github.com/awslabs/aws-sam-local/pull/133 already has code for it)
- [ ] Distribute this package through popular package managers
    - [ ] NPM
    - [ ] PIP

### v0.3.0 Milestone

- [ ] Create a JSON Schema for each AWS service integration. This will allow us to run fuzzing tests against the Lambda function. It will also enable automatically generating POJO-style classes for the event type.

## Backstory - Why this repo?

It all started with a [Twitter thread](https://twitter.com/sanathkr_/status/958402402490527745) on creating examples for CloudWatch Event for Lambda. @stshan had already done the work of downloading the built-in example events from AWS Lambda Console for use with [SAM Local CLI](https://github.com/awslabs/aws-sam-local). After the Twitter thread, it occurred to me that people might want to access to the example events outside of SAM Local. Hence the repository was born. With a separate
repository, we can parallelize the job of adding more events across the developer community and eventually create an exhaustive compendium that is only next best to official.

## Contributors

[Sanath Kumar Ramesh](https://github.com/sanathkr) - Creator & maintainer of this repo

Special thanks to [Jasper Shan](https://github.com/stshan) who originally collected example events from Lambda Console

> Disclaimer: This is **not** an official authority on Lambda Events. We will strive to keep content here as accurate as possible with help of developer community. If you find anything wrong or missing, please do send a Pull Request. We are nice, we promise 😎
