# Socket.IO Chat

A simple chat demo for socket.io

## How to use

```
$ cd socket.io
$ npm install
$ cd examples/chat
$ npm install
$ npm start
```

And point your browser to `http://localhost:3000`. Optionally, specify
a port by supplying the `PORT` env variable.

## Features

- Multiple users can join a chat room by each entering a unique username
  on website load.
- Users can type chat messages to the chat room.
- A notification is sent to all users when a user joins or leaves
  the chatroom.

#step-2

docker build -t chat .
docker run -d --name chat -p 3000:3000 chat

check localhost 3000. it should be working

#step-3
CREATE A repo (as chat or something)
aws ecr get-login-password
--region us-east-1
| docker login --username AWS --password-stdin 903275010366.dkr.ecr.us-east-1.amazonaws.com

use the push commands which will be visible

#step-4 Deployment

1. create the recipes folder.add files (.yml) .
   command -> aws cloudformation deploy --stack-name=production --template-file=recipes/public-vpc.yml --capabilities=CAPABILITY_IAM

Open the stack in cloudFormation console. Check the stack if it's working . wherever the code breaks. Check events etc. Allow those permissions to the IAM User.

2. create another stack . import the public-service.yml file
   set the port as 3000. set counter from 2 to 1. Since, it's not horizantally scalable till now. Image-URL should be the one from Elastic Container Registry. Give names etc.

Once these things are done . CREATE COMPLETE . Go to production stack and check the outputs. We'll get a URL.
This URL can be sent to any person and we can chat with them.

Horizontal scaling .
To solve the problem of users not seeing messages if connected to a different node js process we use Redis .
Redis as a message broker to pass messages between each Node.js process.
