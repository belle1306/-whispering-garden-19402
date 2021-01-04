# bwyd Full Stack App

In this repository, you will use build a full stack Bwyd app using Vue, Node/Express, and MySQL.

## Objectives

- Build a database.
- Build an API server.
- Create a front end.

## Setup

Run `npm install` to install packages.
Run `npm run serve` to run the development server.

### Dependencies

Run `yarn` on root folder to install dependencies related to Express.

`cd client` and run `yarn` install dependencies related to Vue.


### Database Prep

Create `.env` file in project directory and add

```
DB_NAME=bwyd
DB_PASS=YOUR_PASSWORD
```

(replace `YOUR_PASSWORD` with your actual password)

Alternatively, you can rename the provided `.env.example` file to `.env`.

Type `mysql -u root -p` to access the MySQL CLI using your password.

In the MySQL CLI, type `create database bwyd;` to create a database in MySQL.

Run the following in the MySQL CLI: `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'YOUR_PASSWORD';` (replace `YOUR_PASSWORD` with your actual password)

Run `node model/database.js` in your **TERMINAL**, in the **root** folder of your project (not your MySQL CLI! Open a new terminal window for this). This will create a table called 'items' in your database.

### Run Your Development Servers

- Run `yarn start` in project directory to start the Express server on port 5000
- `cd client` and run `yarn start` to start client server in development mode with hot reloading in port 3000.
- Client is configured so all API calls will be proxied to port 5000 for a smoother development experience. Yay!
- You can test your client app in `http://localhost:3000`
- You can test your API in `http://localhost:5000/api`

## Basic Requirements

### 1. Finish the routes

Suggested Process:

- Try and write the correct query in `mysql`.
- Use that query to finish the endpoint in `routes/api.js`.
- Test your endpoint using Postman.

To Do:

- [ ] Use Postman to confirm that you have completed these correctly
- [ ] GET `/api/bwyd` should retrieve all resources.
  - This route is almost complete!
- [ ] POST `/api/bwyd` should create a new resource.
  - To test that your query is correct, check to see if your new resource exists using `mysql`.
  - To test your route, use Postman to see if GET `api/bwyd` returns your new resources.
- [ ] PUT `/api/bwyd/:id` should replace a resource.
  - To test that your query is correct, check to see if your updated resource exists using `mysql`.
  - To test your route, use Postman to see if GET `api/bwyd` includes your updated resources.
- [ ] DELETE `/api/bwyd/:id` should delete a resource.
  - To test that your query is correct, check to see if your resource was deleted using `mysql`.
  - To test your route, use Postman to see if GET `api/bwyd` does not include your new resources.

### 2. Finish the front end

- [ ] Add functionality.
  - Clicking on "Chef" should show the kitchen view, and unclick on "Chef" should show the homepage view.

- [ ] Add styling.
  - The current page the user is on should be clear. Add some conditional styling to the button elements to show this.

![Homepage View](support/homepage_view.png)
![Kitchen View](support/kitchen_view.png)


- [ ] Add functionality.
  - This table should accept a URL, a description, and so on.
  - This table row should have a "add", "delete" and "edit" button.
  - After clicking the button, the image should appear on the page in the Homepage view.
- [ ] Add styling.
  - Everything should be center-aligned. See attached design.
- [ ] Finish the editItem method so it calls the server.
- [ ] Finish the deleteItem method so it calls the server.
- [ ] Add styling.
- [ ] Play with the styling so this looks as professional as possible!

## Resources

- [Vue docs - single file components](https://vuejs.org/v2/guide/single-file-components.html)
- [Vue docs - components](https://vuejs.org/v2/guide/components.html)
- [MySQL Cheat Sheet](http://www.mysqltutorial.org/mysql-cheat-sheet.aspx)
- [MySQL](https://dev.mysql.com/doc/refman/8.0/en/database-use.html)
- [Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
- [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

## Notes

_This is a student project that was created at [CodeOp](http://CodeOp.tech), a full stack development bootcamp in Barcelona._
