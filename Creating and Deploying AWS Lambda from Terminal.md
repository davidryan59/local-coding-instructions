## Creating and Deploying AWS Lambda from Terminal
*Created by David Ryan, March 2019*

*Posted to BEEZ-517, 15th March*


Check `aws` installation
`aws --version`
`which aws`


Install `aws` if you haven't got it:
`pip3 install awscli --upgrade --user`


Check configuration of connection to AWS server via IAM security credentials:
`aws configure`
which brings up prompts:
```
AWS Access Key ID [****************LA2A]:
AWS Secret Access Key [****************e0Eu]:
Default region name [us-east-1]:
Default output format [None]:
```
Use this to check current region and credentials, and enter new ones if necessary. They are stored in:
```
~/.aws/config
~/.aws/credentials
```


Check the list of functions currently available on Lambda:
`aws lambda list-functions`


Update a lambda function that already exists, from a local ZIP package:
`aws lambda update-function-code --function-name LAMBDAFUNCTIONNAME --zip-file fileb://DEPLOYMENTFILE.zip`


Deploy a new lambda function from a local package:
```
aws lambda create-function --function-name LAMBDAFUNCTIONNAME
--zip-file fileb://MYDEPLOYMENTZIP.zip
--handler HANDLERFILE.HANDLERFUNCTION
--runtime python3.7
--timeout 900
--memory-size 3008
--role arn:aws:iam::PROJECTID:role/lambda-s3-role
```
Note:
- You need to specify a role. In this case, the role allows connection to S3.
- For Javascript, use `runtime nodejs8.10`


See:
- [Using AWS Lambda with the AWS Command Line Interface](https://docs.aws.amazon.com/lambda/latest/dg/with-userapp.html)
- [Creating a Deployment Package](https://docs.aws.amazon.com/lambda/latest/dg/deployment-package-v2.html)
- [AWS Lambda Deployment Package in Python](https://docs.aws.amazon.com/lambda/latest/dg/lambda-python-how-to-create-deployment-package.html)
- [Function Guide for `aws lambda` CLI](https://docs.aws.amazon.com/cli/latest/reference/lambda/index.html)
