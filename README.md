# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```console
$ bundle install
$ rails db:migrate db:seed
$ rails s
```

Then, in a new terminal, run the frontend:

```console
$ npm install --prefix client
$ npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged:

### On creating a new toy, the site would render the error:
    NameError (uninitialized constant ToysController::Toys):
### This error occurred because Ruby could not find the class Toys in the index method.
### This was a typo in the code which was handled by calling the Toys class appropriately in the index method
- Update the number of likes for a toy
  - How I debugged:

### On clicking the like button, the action would return the error:
  Uncaught (in promise) SyntaxError: Unexpected token 'P', "Proxy erro"... is not valid JSON
### This error arose from the fact that the method had not yet returned JSON  from the API.
### The error was hence handled by adding a line of code that would render the toys variable in the creae method in json format.


- Donate a toy to Goodwill (and delete it from our database)
  - How I debugged:

### After clicking on the 'Donate to Goodwill' button, the rails server rendered the:
  ActionController::RoutingError (No route matches [DELETE] "/toys/1")
### This meant that no route had been provided for the DELETE method
### therefore, a ':destroy' route was added on the resources in routes. rb.
### This allowed the delete function on the site's toys which meant a toy has been donated to Goodwill.


