---
layout: post
title: Deploy your first Serverless API
date: 2020-10-16 00:00:00
lang: en
ref: deploy-your-first-serverless-api
description: 
comments_id: 
---

So far we've configured our AWS account and AWS CLI. We've also created our Serverless Framework app. A big advantage with Serverless is that there isn't any infrastructure or servers to provision. You can simply deploy your app directly and it's ready to serve (millions) users right away.

Let's do a quick deploy to see how this works.

{%change%} In your project root, run the following.

``` bash
$ serverless deploy
```

The first time your Serverless app is deployed, it creates a S3 bucket (to store upload your Lambda function code), Lambda, API Gateway, and a few other resources. This can take a minute or two.

Once complete, you should see something like this:

``` bash
Service Information
service: notes-api
stage: prod
region: us-east-1
stack: notes-api-prod
resources: 11
api keys:
  None
endpoints:
  GET - https://0f7jby961h.execute-api.us-east-1.amazonaws.com/prod/hello
functions:
  hello: notes-api-prod-hello
layers:
  None
```

Notice that we have a new GET endpoint created. In our case it points to — [`https://0f7jby961h.execute-api.us-east-1.amazonaws.com/prod/hello`](https://0f7jby961h.execute-api.us-east-1.amazonaws.com/prod/hello)

If you head over to that URL, you should see something like this:

``` bash
{"message":"Go Serverless v2.0! Your function executed successfully! (with a delay)"}
```

You'll recall that this is same output that we received when we invoked our Lambda function locally in the last chapter. In this case we are invoking that function through the `/hello` API endpoint.

We now have a Serverless API endpoint. You only pay per request to this endpoint and it scales automatically. That's a great first step! 

Now we are ready to write our backend code. But before that, let's create a GitHub repo to store our code.
