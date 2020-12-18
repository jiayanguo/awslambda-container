
# Description
----
This is for demo how aws lambda work with docker container.

### Build docker image
```
docker build -t awslambda-container .
```

### Run docker container locally for test
```
docker run -p 9000:8080 awslambda-container:latest
```

### Now it's time to test
```
curl -XPOST "http://localhost:9000/2015-03-31/functions/function/invocations" -d '{"value": "This is test data"}'
```

### Now, let's push the image to ECR
```
docker tag awslambda-container:latest <account-id>.dkr.ecr.us-west-2.amazonaws.com/awslambda-container:latest
docker push <account-id>.dkr.ecr.us-west-2.amazonaws.com/awslambda-container:latest
```

### Create aws lambda and add api gateway as trigger.
https://9pucpnqwz1.execute-api.us-west-2.amazonaws.com/default/mytestFunc

**Reference:**
https://aws.amazon.com/blogs/aws/new-for-aws-lambda-container-image-support/