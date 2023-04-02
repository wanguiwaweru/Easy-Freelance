# Easy Freelance

Easy freelance is a web-application that allows freelance developers to organize and monitor the projects they are working on at a given time.

The application provides an easy to use interface allowing users to add project and client details.

It uses modern frontend and backed development tools.

## ⚙️ Features and Interfaces

1. Home page

    * Shows all the projects and their completion status.
    * Shows all the clients.
    * The user can add a new client or a new project.
    * The user can delete a client. The projects associated with the deleted client are also deleted.

2. New Client Page

    * Allows user to add client details including their name,email, and phone number.

3. New Project Page

    * Allows user to add project details including their name,description,completion status and name of the associated client.
    * The user selects the project's client from a drop down because a project has to be associated with a client.

4. Update Project Details Pages.

    * Shows the project details including the name, description, completion status,and client information.
    * Users can change the project details as needed.

<img src="client\src\components\assets\home page.jpg" alt="Add client" style="height: 500px; width:800px;"/>

<img src="client\src\components\assets\add client.jpg" alt="Add client" style="height: 400px; width:400px;"/>
<img src="client\src\components\assets\add project.jpg" alt="Add project" style="height: 400px; width:400px;"/>

<img src="client\src\components\assets\update project.jpg" alt="Add client" style="height: 600px; width:800px;"/>

## Built With 

* Nodejs
* Express
* MongoDB
* React
* GraphQL

## Getting Started

### Prerequisites

* NodeJS version 18+

* [MongoDB Atlas account](https://www.mongodb.com/cloud/atlas/register)

To get started, clone the repo and navigate to the server folder using the `cd server` command.

On your terminal run `npm install` to install the dependencies.

Set the environment variables in a .env file. This file will contain the Port number and the MONGO_URI obtained from your MongoDB instance.

Then run `npm start` to start the server.

On another terminal window navigate to the client folder using the `cd client` command.

Run `npm install` to install the dependencies and run `npm start` to start the client.

Navigate to http://127.0.0.1:3000/ to view the application.

## GraphQL Queries and Mutations 

To test the GraphQL queries and mutations, navigate to http://localhost:5000/graphql.

> You can modify the port number based on the number you provided in the .env file.

1. #### Create a new client 
```
mutation {
  addClient(name: "Lee Child", email: "leechild@gmail.com", phone: "0724156378") {
    id
    name
    email
    phone
  }
}
```

2. #### Delete a client
```
mutation {
  deleteClient(id: 4556) {
    id
  }
}
```

3. #### Create a new project.

```
mutation {
  addProject(name: "Chat bot", description: "Build a Whatsapp bot for customer engagement", status: new, clientId: "") {
   name
   description
   status
  }
}
```

4. #### Update project status and return name,description and status
```
mutation {
  updateProject(status: "completed") {
   name
   status
  }
}
```

5. #### Get all clients
```
{
  clients {
    name
    email
    phone
  }
}
```

6. #### Get a single client
```
{
  client(id: 1) {
    name
    phone
  }
}
```

7. #### Get all projects
```
{
  projects {
    name
    description
    status
  }
}
```
8. #### Get one project
```
{
  project(id: 1) {
    name
    description,
    client {
      name
      email
    }
  }
}
```