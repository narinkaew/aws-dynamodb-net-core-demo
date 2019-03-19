# aws-dynamodb-net-core-demo

First, pull DynamoDB docker image down to your local machine via command

> docker pull amazon/dynamodb-local

Then run the container in detached mode

> docker run -p 8000:8000 -d amazon/dynamodb-local

Finally, running the sample application with the SDK configured to use the local DynamoDB Docker container

Note, you need to have configured the credentials for the .NET SDK to be able to connect to AWS and change the appsettings config to connect to the actual AWS service when you need to work with AWS DynamoDB.
