---
layout: "post"
title: "Federated Learning"
author: "Zanark"
tags: machine-learning tutorial
---

Hey all! Happy New Year! 2020!!

So I've been working on my machine learning skills which are pretty much non existent, and now I have been assigned a new task by my mentor...which is to learn  how federated learning works. So I'm just gonna document what I learned here. Hope its informative ^_^

# Federated Learning

## What is federated learning?

In federated learning the data is decentralised. This means that the data provided to the model is recieved from different sources simultaneously. For example getting data for a model form different mobile devices.

## Why federated learning?

Conventionally, the machine learning model works on the server and data is provided to the server by different clients. However this has some limitations:

1. The server is online therefore poor internet will cause latency in getting results from the server, and such a case is not ideal for a model aiming for real-time results.
2. The application cannot work offline.
3. The network over which the data is sent is not secure enough therefore sensitive data can get leaked.
4. Sending and recieving data over a network is expensive for the battery and for the user as it'll take up a lot of data.

Well, what if the model is on the phone? This way teh model and the data is inside the moile phone.Well that has its own limitations as well:

1. There's not enough data for the model.
2. Training and testing can use up a lot of battery.

Eg: What if a new word gets introduced in the dictionary and everyone else is using it but the user, this way the user doesn't have the data for that word locally and the model will never know about it, and therefore this feature will never get discovered by the user unless he gets to know about it from an external source.

Well then, what if the model is pretrained a bit on the server using some proxy data, and then is sent to the clients for further training.

This solution might sound optimal but we can never decide on the perfect proxy data that can be used to pretrain the model.


So in essence federated learning is kind of like collaborative learning.


Here the server send an initial model(which is not pretrained on any data) to all the clients. The clients then train and test the model on their own local data. When all the clients are done with trainig their models, their modified models is then pushed to the server which then takes an average of the modified model and send it back to the clients. So as you can see, we have a cycle here.

## Now about Privacy..

One of the reasons why federated learning is so successfull is that it handles privacy really well.

- The data never left the clients device => sensitive data was never shared over the network => secure
- You can trust the servers.
- Server cannot log any data from the clients.
- Differential Privacy: Each client adds some noise to the data they provide to the server. With a large number of clients, the noise generated on the server-side creates a mask over the data it recieves which makes it difficult to point out individuality of the data still maintaing the progressibilty of the data.

