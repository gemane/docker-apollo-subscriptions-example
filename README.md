## docker-compose installation using repositories from GraphQL College (GraphQL Subscriptions with React, Node, Apollo and Postgres)

The docker container clone code from ["Pinterest style app built with Apollo subscriptions"](https://www.graphql.college/graphql-subscriptions-with-react-node-apollo-and-postgres/) to start a multi-container application which is using the technologies: React, GraphQL, Apollo, Express, NodeJS, Postgres and Websocket.

The code is cloned from the following repository into two separated containers (client, server)

* [Apollo Subscriptions Example](https://github.com/GraphQLCollege/apollo-subscriptions-example)

Additionally a container with a Postgres database will be initiated and one where Nginx is running.

## Requirements 

You should have docker and docker-compose installed on your machine.

## Installation 

* Clone the project from the repo, 
* build your project using

``` 
$ docker-compose build
``` 

* and/or run the following command directly inside the directory

 ```
 $ docker-compose up -d
 ```

* After starting all container the database must be initialized manually

``` 
docker exec -it api yarn db:create
docker exec -it api yarn db:migrate
``` 

 Your project will run in the browser as

* Web App with React at 
  + http://localhost:3000/

* API as NodeJS project with GraphQL at 
  + https://localhost/graphiql

* Websocket at
  + wss://localhost:443/subscriptions

## Deployment

Included is a deployment script `deployment-apollo-subscriptions-example.sh` so that the application can be started easily. 

Be careful as this script 

* stops all relevant container
* deletes all exited container
* deletes unused images
* deletes orphaned volumes
* and deletes orphaned network nodes.

Finally it builds and starts up all docker images.
