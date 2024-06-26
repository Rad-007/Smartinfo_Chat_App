# Django-Chat Application for SmartInfo
Creating a realtime group chat app using Django-channels and Redis server




## Features

- Basic signup/login using Django's default classes
- Admin can create chat rooms
- Users can chat in their chat rooms after choosing a chat room
- Chat messages are stored in Redis during the chat and also in sqlite database.(Postgres db is being comented out can create new database for locals Postgres System)
- [users.txt](https://github.com/Rad-007/Smartinfo_Chat_App/blob/8ca1d477eec66dc0ebe0a2ba8bb46669e4c3e156/users.txt) file contains the list of users in the chat app including their usernames and passwords.
- New Users can be created on in ignup/Loin
## Communication Mechanism

The channel layer is a communication system that allows multiple consumer instances to talk with each other.

A channel layer offers several key abstractions:

1. **Channel**: A mailbox for sending messages. Messages can be sent to a channel using its name. Every consumer instance has a unique channel name, generated automatically.

2. **Group**: A collection of related channels identified by a name. Participants can add or remove channels from the group using the group's name. Messages sent to the group are broadcasted to all channels in it. 

In the context of a chat application, the goal is to enable multiple instances of `ChatConsumer` within the same chat room to interact. This is achieved by having each `ChatConsumer` add its channel to a group named after the room. By doing so, messages sent to the group are received by all `ChatConsumers` in that room.

To implement this, a channel layer that uses Redis as its underlying storage mechanism is used. Redis provides the infrastructure to manage these channels and groups, enabling efficient message distribution among participants.

## Environment
- Python 3.9
- Librarires to install
  
  ```shell
    pip install -r requirements.txt
  ```
- Extra libraries
    - Django-channels:

    ``` shell
    $ python -m pip install -U 'channels[daphne]'
    ```
    - *channels_redis* so that Channels knows how to interface with Redis
    ``` shell
    $ python3 -m pip install channels_redis
    ```
- Redis server is run on *docker*. So, docker has to [installed](https://docs.docker.com/desktop/install/ubuntu/)

```shell
$ python3 -m pip install channels_redis
```
## Instructions
- Run Redis server of Docker
```shell
$ docker run --rm -p 6379:6379 redis:7
```
- Run Django-Chat app
```shell
$ python manage.py runserver
```

## Reference
- [Python Django Realtime Chat Project](https://www.youtube.com/watch?v=SF1k_Twr9cg)

