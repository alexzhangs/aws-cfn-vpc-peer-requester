# aws-cfn-vpc-peer-requester

AWS CloudFormation Stack for VPC Peering Requester.

## Usage

### stack.json

This repo contains a standard AWS CloudFormation template `stack.json`
which can be deployed with AWS web console, AWS CLI or any other AWS
CloudFormation compitable tool.

This repo can be used along with below repoes:

* [aws-cfn-vpc-peer-accepter](https://github.com/alexzhangs/aws-cfn-vpc-peer-accepter)
* [aws-cfn-vpc](https://github.com/alexzhangs/aws-cfn-vpc)

To create cross account VPC peer connections, one accepter peers with
multi requesters. These repoes may make the process easier.

However you will need to make a new template to put all these together,
put `aws-cfn-vpc`, `aws-cfn-vpc-peer-accepter` and
`aws-cfn-vpc-peer-requester` as the nested stack of your new stack.

About how to do this, you may refer to a real world example
[aws-cfn-vpn](https://github.com/alexzhangs/aws-cfn-vpn), which put
all these together, and is able to create one(accepter) to many(requester) cross
account VPC peer connections.

This template will create an AWS CloudFormation stack, including
following resources:

* 1 peer connection between 2 VPCs.
* 1 route entry in the route table for the peer connection.
* 1 IAM role to give the Lambda function necessary permissions for the
SQS, and the logs.
* 1 Lambda function to send SQS messages to trigger the Lambda funcion
  in another VPC.
* 1 CloudFormation Custom Resource to trigger the Lambda function of
this stack.

For the input parameters and the detail of the template, please check the template
file.
