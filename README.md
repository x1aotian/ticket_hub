# Wel come to x1aotian's TickectHub

TicketHub is a ticket resale website built by microservices. \
Users are required to log in with their accounts. And then they can buy or sell tickets with customzied prices. \
Thie readme file will provied basic set-up steps for this application, and then help go through all modules.

## Setup
1. Install `npm`. Go to each sub directory and run `npm install`.
2. Install `docker` and enable `Kubernetes`.
3. Install `skaffold` and `NGINX ingress` controller.
4. (Optional) If you want to run this application in GCP instead of local environment,\
please connect deploy contariners to GCP using `Kubernetes clusters` and `Cloud Build`. This [tutorial](https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster) can be refered.
5. Run `skaffold dev` to start the application.
6. (Optional) To run test, Go to each sub directory and run `npm run test`.

## Modules Overview
### `./client`
Client is the front-end client-side module built using `react`. \
It handles logics of frontend components and sends correcrt requests to other backend moduels. \
As this project focus on backend mricoservices. The website design is pretty simple. No worries - I'll make them more fancy later.

### `./common`
Common integrates common-used functions as middlewares for different purposes, \
including errors handlers, events listener / publisher and authtication middlewares.

### `./auth`
Module for authentication. We use`JWT` and cookies to do auth in this application.

### `./nats`
Libraray `NATS` streaming server is used to build event bus. \
We use publisher-listener constructure to realize the functionality of event bus.

### `./tickets` and `orders`, 
Logics of tickets and orders are included in these two modules.

### `./payments`
Module to process payments. `Stripe` is used as the third-party payment application here.

### `./expiration`
Module to handle expiration. It emphysizes a lot on OCC (Optimistic Concurrency Control).
