# Zendesk-Coding-Challenge
#An Express Server (Backend) that retrieves paginated (25 at at time) tickets using the Zendesk API and redirects the tickets to the React frontend.

<img src="Tickets Screen.png" width="1000" height="600">
<img src="Pagination Screen.png" width="1000" height="600">
<img src="Detailed Ticket Screen.png" width="1000" height="600">


# Installation
## Step 1 : Setting up the project and dependencies
- Download a zip file or clone the repository to your local machine.
- From the root of the folder, change the directory to backend and run `npm i` to install the backend dependencies.
- From the rooe of the folder, change the directory to frontend and run `npm i` to install the frontend dependencies.

## Step 2 : Running the Backend
- Migrate to the backend directory.
- Run the command  `node server.js` to run the server. (The server runs on PORT 4000).

## Step 3 : Running the Frontend
- Using another terminal, migrate to the frontend directory.
- Run the command  `npm start ` to run the frontend. (The frontend runs on PORT 3000)

## Step 4 : Accessing the Frontend
- Go to any browser application and load `http://localhost:3000/` to see the application live in action!


# Tech Stack
## Frontend - React
One of my prime reasons to use react as my frontend was due to the dynamic nature of the coding challenge. As paginated data had to retrieved and displayed on the frontend everytime the user clicked on the prev or the next buttons, I believe that using react is a simple and effective way to manage the data in the frontend. Moreover, The react hooks like useState and useEffect can update the frontend components everytime the ticket data changes.

## Backend - Node.js + Express
Using a node server like express enabled me to maintain a clean an efficient code at the backend. Express makes it very east to sort of distinguish the different endpoints that the server serves. On top of it, the node environment enabled me to use HTTP libraries like Axios which works on the mechanism of promises and eliminates the need of asynchronous functions.


# Design of the application
## When the main screen loads
- When the `http://localhost:3000/` is loaded in the browser, the frontend is triggered.
- The frontend makes a GET request to the server running on `http://localhost:4000/` by hitting the `/` endpoint of the server.

Clicking a ticket will display additional information in a modal. To close the modal, the user can use the close button, click the background or press the escape key.

The tickets are paginated, showing 25 tickets per page, with a pagination bar at both the top and bottom of the Ticket List.


