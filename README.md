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
## When the Main Screen loads :
- When the `http://localhost:3000/` is loaded in the browser, the frontend is triggered.
- The frontend makes a GET request to the server running on `http://localhost:4000/` by hitting the `/` endpoint of the server.
- The server then makes an API call to the Zendesk endpoint.
- The API responds to the server by sending the data in JSON format.
- The server then redirects the data to the frontend.
- As soon as the frontend gets the JSON data, it maps this list of tickets to a Ticket Component and renders the screen.

## When the Navigation buttons are clicked : 
- Whenever the user clicks on the next or the prev buttons, the frontend initiates a GET request to the server at the `/next` endpoint.
- The server in turn initiates a GET request for the next 25 tickets that are to be served from the Zendesk API.
- The API responds to the server by sending the data in JSON format.
- The server then redirects the data to the frontend.
- As soon as the frontend gets the JSON data, it maps this list of tickets to a Ticket Component and renders the screen.

## When an individual ticket component is clicked
- Whever the user clicks on an individual ticket, the frontend initiates a GET request to the server at the `/ticket` endpoint.
- The server in turn initiates a GET request for the ticket data that was clicked by the user.
- The API responds to the server by sending the data in JSON format.
- The server then redirects the data to the frontend.
- As soon as the frontend gets the JSON data, it maps this data to the Detailed Ticket Component.

# Design Decisions
## For the Main Screen
Just before the frontend is rendered when the user loads the `http://localhost:3000/`, the frontend makes a get request to the server at the '/' endpoint. I chose this implemenation because, it avoids any asyncronization between the backend and the frontend components. Thus, Ensuring that the frontend componenets would only be loaded whenever the data is available to the frontend.

For the main screen, the backend requests only for the first 25 tickets in order to implement pagination.

## Pagination
In order to implement pagination in an effective way, whenever the Main screen is loaded or the user clicks on the next and previous buttons the frontend makes a GET request to it's approriate endpoint in the backend. The backend in turn makes a GET request to the zendesk API to fetch the next 25 or the previous 25 tickets.

I chose this design after considering all other alternatives. One alternative was to load all the tickets at once and then page through the data in the frontend but I believe that this design is not scalable and won't be appropriate given the dynamic nature of the coding challenge use case.

The tickets may update dynamically as fast as every second and in order to cope up with the speed and dynamic nature of the data, it is best to make an API call everytime the user clicks on the next or prev buttons or loads the main screen. This is because, making an API call would serve the updated data rather than showing tickets that may already have been resolved. Moreover, This implementation is much more scalable as request is made for only 25 tickets at once. If we were to load all the tickets for an account having millions of tickets, the frontend pagination method fails to provide a good UX to the user due to the long loading time. 



