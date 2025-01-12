# PYTHON-PROJECT
Overview
This Python project implements a simple HTTP server that exposes a RESTful API to interact with a real estate database. The API provides access to resources such as owners, properties, agents, property viewings, and sales. The data is fetched from a MySQL database, and the response is formatted as JSON.

The server is built using Python's http.server and handles HTTP GET requests. It uses a custom JSON encoder to ensure proper serialization of datetime and Decimal data types.

Features
Retrieve data for owners, properties, agents, property viewings, and sales.
Retrieve specific records by ID or all records for each resource.
Responses are returned in JSON format.
Custom JSON encoder for handling datetime and Decimal data types.
Handles errors such as resource not found (404) and server errors (500).
Requirements
Python 3.x
MySQL database
mysql-connector-python package to interact with MySQL
Dependencies
To install the required dependencies, run the following command:

bash
Copy code
pip install mysql-connector-python
Database Configuration
The database connection settings are stored in the DB_CONFIG dictionary. You will need to update these values based on your MySQL configuration:

python
Copy code
DB_CONFIG = {
    "host": "localhost",  # Your database host
    "user": "root",       # Your database username
    "password": "root",   # Your database password
    "database": "realestate"  # Your database name
}
Make sure your MySQL database contains the necessary tables (owners, properties, agents, property_viewings, and sales), or adjust the schema as needed.

API Endpoints
The server provides the following endpoints:

1. GET /owners
Fetches all owners from the database.

2. GET /owners/{owner_id}
Fetches a specific owner by their owner_id.

3. GET /properties
Fetches all properties from the database.

4. GET /properties/{property_id}
Fetches a specific property by its property_id.

5. GET /agents
Fetches all agents from the database.

6. GET /agents/{agent_id}
Fetches a specific agent by their agent_id.

7. GET /property_viewings
Fetches all property viewings from the database.

8. GET /property_viewings/{viewing_id}
Fetches a specific property viewing by its viewing_id.

9. GET /sales
Fetches all sales from the database.

10. GET /sales/{sale_id}
Fetches a specific sale by its sale_id.

Running the Server
To run the server, execute the script server.py:

bash
Copy code
python server.py
By default, the server will run on port 8080. You should see the following message indicating the server is running:

arduino
Copy code
Server running on port 8080...
Once the server is up, you can use any HTTP client (e.g., curl, Postman, or a web browser) to interact with the API.

Example Requests
Fetch all properties:
bash
Copy code
curl http://localhost:8080/properties
Fetch a specific owner by ID:
bash
Copy code
curl http://localhost:8080/owners/1
Fetch a specific property by ID:
bash
Copy code
curl http://localhost:8080/properties/1001
Error Handling
404 Not Found: If the requested resource does not exist, the server will return a 404 status code with a JSON error message:

json
Copy code
{
    "error": "Resource not found"
}
500 Internal Server Error: If an exception occurs during processing, the server will return a 500 status code with the error message.

Custom JSON Encoding
The CustomJSONEncoder class is used to handle special types of data that need to be serialized differently:

Date and datetime objects are converted to ISO 8601 strings.
Decimal objects are converted to floating-point numbers.
Closing Notes
Ensure that your MySQL server is running, and that the realestate database is set up with the required tables (owners, properties, agents, property_viewings, and sales).
You can extend the server to handle additional endpoints or modify the database schema to fit your needs.
