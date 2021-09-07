# Test Task

The aim of the Test Task is to develop a small Todo List application.
The backend is Hasura, a GraphQL engine based on a Postgres database. New todos can be added to the already existing table "todos" via the Hasura Console.

The Angular app is to be created in the "app" folder and the Apollo client and the Material UI are to be integrated.

The goal is to query all todos via a websocket connection and then subscribe to them (a GraphQL subscription must be used for this). Each new entry in the table should be displayed automatically (without reloading the application) in the Angular app.

The app should be set up as simply as possible. The design does not play a role either, only the function and structure of the Angular app is important.

## Prerequisites

1. Docker & Docker Compose should be installed on the system to run hasura.
2. yarn should also be installed.

## Start Hasura Server

1. The server can be started with `yarn hasura:start`
2. After that, `yarn hasura:migrate` must be executed, to apply existing migrations
3. Open Hasura console: `yarn hasura:console`

## Hints

- To authenticate to hasura using the admin secret, you could use the following WebSocket link:

```
const wsLink = new WebSocketLink({
  uri: "ws://localhost:8080/v1/graphql",
  options: {
    reconnect: true,
    connectionParams: {
      headers: {
        "x-hasura-admin-secret": "codestryke",
      },
    },
  },
});
```
