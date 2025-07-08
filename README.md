# Flight Tracker
ABSTRACT

This report will detail the design and implementation of the third project which is a web app for real-time flight tracking. The app is titled “Flight Tracker”. If users enter the call sign of the flight they want in the search section, they will access all information about the flight. Python and Open Sky API were used in the development of the project. The development process, like other flight tracking applications, consists of searching for flights and connecting to the API, and displaying the data we want on the user screen. The application was created using a simple interface so that everyone can use it comfortably. In this report, the reader will see a detailed overview of the project and our solution for it.
 
 
INTRODUCTION

Flight Tracker is a web application developed to provide users with current flight information. Utilizing the Flask web framework and the OpenSky Network API, the application allows users to input a flight call sign and retrieve key details such as the flight's call sign, origin country, longitude, latitude, altitude, velocity, heading, vertical rate, and live location on the map. The application uses Folium to generate a map displaying the flight's position.
  The primary aim of this project is to create a tool that assists travelers, aviation fans, and researchers in tracking flights in real time. It goals to provide a simple user experience by displaying flight information and visualizing the flight's location on an interactive map.
 

Target Users

  Travelers: Individuals wanting to track their flights or those of their friends and family.
  
  Aviation Fans: People interested in following flights.
  
  Researchers: People who need real-time flight data for analysis or study, such as academics and professionals.
  

Functional Requirements

  There are some functional requirements for Flight Tracker to work. The first one is user input. The application provides a search box for users to enter the flight call sign and this call sign is the part that interacts with API. The application interacts with the OpenSky Network API to fetch real-time flight data. The data that fetch such as coordinates, altitude, speed, and origin country are displayed in a structured format. One of the fetched data is coordinate, and this is used for map visualization. An interactive map shows the current location of the flight. The last requirement is error handling. The system handles cases where the call sign is incorrect, or the flight data is unavailable.


Technical Specifications

  Programming Language: Python 3
  
  Framework: Flask
  
  API: OpenSky Network API
  
  Mapping Library: Folium
  
  HTML/CSS: For the web interface
  
  Development Tools: Visual Studio Code


Key Components

  HTML Template: Defines the structure and style of the web page.
  
  fetch_flight_data Function: Retrieves flight data from the OpenSky API.
  
  create_map Function: Generates an interactive map using Folium.
  
  Flask Routes: Handles HTTP GET and POST requests, rendering the template with flight data and the map.
  
Note: Since OpenSky API was the only free option, we used it, but since it is a model that is constantly maintained, we wanted to mention the problems it caused during the process in our report.
 
 
HOW IT WORKS

  The code that is provided consists of a Flask application that includes a simple HTML template for the implementation of the user interface, the functions to fetch flight data from the OpenSky Network API, and generates a map showing the flight's location. Below is a detailed breakdown of the code:


1.User Interface:

  The application features a simple and user-friendly web interface where users can enter a flight call sign in a search box.
  
  The interface is structured with HTML and styled with CSS to ensure a clean and responsive design


2.Flight Data Fetching:
  
  Upon the user submitting the form, the application sends a request to the OpenSky Network API to retrieve flight data corresponding to the provided call sign.
  
  The API response is processed to extract relevant flight information, including the call sign, origin country, latitude, longitude, altitude, velocity, heading, vertical rate, and live location on the map.

3.Map Integration:
  
  If valid flight data is received, the app uses Folium to create an interactive map showing the flight's current location.
  
  A pointer is added to the map to display the flight's position.


4.Rendering the Response:
  
  The web page was created dynamically using an HTML template.
  
  The template includes a search bar for entering call signs, a search button for submission, placeholders for flight data, and the map populated based on API response.
 

Implementation Details
  
  1. Imports:
    
  Flask and related modules for web development.
    
  Folium for map creation.
    
  Requests for making HTTP requests to the API.
    
  Logging for debugging and monitoring.
 
  
  2. HTML Template:
  
  Defines the structure of the web page including form elements and placeholders for flight information and the map.
  
  CSS codes of the elements that make up the appearance of the web page are also found here.

  
  3. fetch_flight_data Function:
  
  Makes an HTTP GET request to the OpenSky API using the provided flight call sign.
  
  Parses the response to extract relevant flight data.
   
  
  4. create_map Function:
  
  Creates an interactive map using Folium centered on the flight's current latitude and longitude.

  
  5. Flask Routes:
  
  / Route: Handles both GET and POST requests. On form submission, it fetches flight data and generates a map if data is available.
   
  
  6. Main Block:
  
  Configures logging and starts the Flask development server.
  
  
  7. User Input Handling:
  
  The application allows users to input a flight call sign through a form. This user input is critical as it serves as the basis for retrieving specific flight data.
  
  
  8. Form Submission:
  
  The HTML form is submitted via POST request when the user enters a call sign and clicks the "Track Flight" button.
  
  The submitted call sign is retrieved using request.form['callsign'].
  
  
  9. Validation and Data Fetching:
  
  The fetch_flight_data function is called with the submitted call sign.
  
  The function performs an HTTP GET request to the OpenSky Network API endpoint. If the API response status is 200 (OK), the response data is parsed to extract flight information. If no exact match is found or the response is invalid, a warning is logged, and no data is returned.
  
  
  10. Display of Flight Information:
  
  Once the flight data is retrieved from the API given it is a valid flight that the user is searching for, it is directly displayed to the user in a structured format for better understanding.
    
  
  11. Extraction of Flight Information:
  
  Relevant details are given to the user such as callsign, origin country, longitude, latitude, altitude, velocity, heading, and vertical rate. These details are made available by formatting the data API collects and sends.
   
  
  12. Conditional Rendering:
  
  The HTML template uses Jinja2 templating to conditionally render flight information and the map. If flight info is available, it is displayed in an unordered list (ul). If flight info is not available, a message that indicates the unavailability of data is shown and the user is able to enter another callsign.
  
  
  13. Interactive Map Generation:
  
  When the user enters a call sign location data requested from the API is transferred to our map function which is a separate functionality we have implemented independent of the API and ultimately generates an interactive map to visualize the flight's current location.
  
  
  14. Map Creation:
  
  The create_map function is called with the flight's coordinates, its latitude, and longitude.
  
  Folium is used to create a map that shows the coordinates provided by the plane.
  
  The flight's current location is indicated by a marker that’s placed on the map using the coordinates of the plane.
  
  The map is converted to an HTML string using map_obj._repr_html_() to be implemented into the page we have created.
  
  
  15. Map Rendering:
  
  If map_HTML is available, the map is embedded in the HTML template and displayed to the user. In the event that there is no coordinate data the map will be not shown but the rest of the functions will proceed so the code is able to proceed without encountering any errors.
  
  
  16. Logging and Debugging:
  
  The application employs logging for debugging and monitoring to confirm whether the problem is user or application-sided if any problems occur. 
  
  
  17. Logging Configuration:
  
  The logging level is set to INFO to capture detailed information about the application's operations and display it inside the terminal.
  
  Log messages are generated for key events in the process such as API requests, data retrieval, and error occurrences.
  
  
  18. Usage in Functions:
  
  Log messages provide insights into the API URL being accessed, the data fetched, and any issues encountered (e.g., no exact match for the call sign), they can be viewed simultaneously through the terminal if the user is interested in further knowledge.
