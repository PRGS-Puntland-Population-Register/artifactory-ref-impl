# artifactory-server

This is a refeference implementation of artifactory service used within MOSIP. The artifactory service contains the dynamically loaded libraries and services. The current repository is a reference implementation of the artifactory service and it packages the necessary mocks, reference implementation to run the default version of MOSIP.

Following are the artifacts which is being served by the service:
  1. Auth-adapter.jar
  2. Ref-Idobjectvalidator.jar
  3. Biosdk.zip
  4. hsm client
  5. cache jar
  6. sms-notification.jar
  7. clamav-antivirus.jar

All these artifacts are released as a part of the Mosip Release with some of them being taken from open sourced repository as per the need.


# Update / Deplo
Apply the changes you want to deploy.
```shell
aws ecr get-login-password --region eu-west-1 --profile garowe-prod| docker login --username AWS --password-stdin 767397757018.dkr.ecr.eu-west-1.amazonaws.com

VERSION=1
docker build -t mosip/artifactory-server:${VERSION} .
docker tag mosip/artifactory-server:${VERSION} 767397757018.dkr.ecr.eu-west-1.amazonaws.com/mosip/artifactory-server:${VERSION}
docker push 767397757018.dkr.ecr.eu-west-1.amazonaws.com/mosip/artifactory-server:${VERSION}
```