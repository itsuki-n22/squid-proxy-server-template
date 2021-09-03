# Squid Proxy Server Template

This is a template makes it easy to get started with Proxy Server by using AWS Cloud Formation.

Region code is below
https://docs.aws.amazon.com/ja_jp/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-available-regions

## USAGE
### Start and Activate Server
0. download AWS CLI
1. edit params.cfg
2. `aws --region <region-code> cloudformation deploy --stack-name <arbitary-stack-name> --template-file template.yml --parameter-overrides $(cat params.cfg)`

### example:
`aws --region us-west-1 cloudformation deploy --stack-name squid --template-file template.yml --parameter-overrides $(cat params.cfg)`

### Delete Server
`aws cloudformation delete-stack --stack-name <arbitary-stack-name>`

## Explanation of params.cfg
The following is an example.
```
PORT=3128  # port number used for proxy server
KEYNAME=some-ec2-key # EC2 instance key pair !CAUTION! you must make key pair on target region
Service=squid-1  # Name for EC2 Name Tag 
AllowedIP='123.456.789.10/32' # input IP you are using now
AZ=us-west-1b # availability zone 
```

You can check your IP by using below command. 
```
curl https://checkip.amazonaws.com
```
