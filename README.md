##Highcharts Image Export Amazon Elastic Beanstalk
================================================

Simple solution to creating Highcharts Export server using Amazon EC2 Elastic Beanstalk

We've have been building a rich client app on the .NET platform using Highcharts graphing throughout and have 
tried using the .NET solution as suggested on the Highcharts install page. 

This worked for the most part but we were plagued with minor rendering issues, labels wouldn't align, 
borders would appear, date entry fields were overlapped, legends would stop rendering as soon as the 
renderer encountered any HTML to name but few. We were sure this was all to down to the SVG.dll, we could post 
the same to the Highcharts export server and all would render as expected. 

That left us with the problem of trying to bring Java/Batik into
our Windows landscape. We didn't want to dirty our production servers with Java and PHP so looked for 
an alternative and this solution fitted the bill.

The following describes how to set up a Highcharts export server using Amazons Elastic Beanstalk:
http://aws.amazon.com/elasticbeanstalk/

To get up and running with your own Highcharts export server hosted in Elastic Beanstalk follow the steps below.

###Pre-requistites: 
1. Git installed.
2. Pwershell 2.0 installed.
3. An AWS account with permission to create Beanstalk applications.
4. The Amazon Access Key Id and Secret Access Key for the account above.

###Steps:
1. Download and install the Amazon Beanstalk CLI - http://aws.amazon.com/code/6752709412171743
2. Extract and run the AWSDevTools\Windows\AWSDevTools-OneTimeSetup.bat (Which sets up the Powershell modules)
3. Now run the file AWSDevTools-RepositorySetup.bat in your cloned version of this repo (Or update with newer version if version numbers differ)
4. Now configure your AWS credentials for GIT by running: git aws:config, this will ask for the following details:
	1. AWSAccessKeyId
	2. AWSSecretKey
	3. AWS Region (Just leave as default)
	4. AWS Elastic Beanstalk Application (The name of your application)
	5. AWS Elastic Beanstalk Environment (The environment name, you can have multiple, STAGING, PROD etc)
	This then stores your credentials locally, creates the Beanstalk app, Environment EC2 instance, Loadbalancer, Beanstalk Security Group 
	and a nice http://<AWS Elastic Beanstalk Environment>.elasticbeanstalk.com address to access your application. 
	Our failed a couple of time to create the environment but create everything else, we just created the env with the same name from 
	within the console.
5. Now run git aws.push from the root of your local repository, this will copy the files to the environment.
6. Make a cup of tea, come back, done.