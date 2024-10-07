# IdeaAPI-Automation-Testing

This project tests the IdeaAPI through Postman requests. The following endpoints are tested:

- Login and Authentication
- Create a New Idea
- List all Ideas
- Edit the Last Idea
- Delete the Edited Idea
  
## Table of Contents

- Project Overview
- Technologies Used
- Installation and Setup
- Postman Collection
- Tested Endpoints
     - Login and Authentication
     - Create a New Idea
     - List all Ideas
     - Edit the Last Idea
     - Delete the Edited Idea
- Running the Tests
- License
  
## Project Overview

The "IdeaAPI-Automation-Testing" project demonstrates API testing using Postman to verify key functionalities for managing ideas such as creating, editing, and deleting ideas. Authentication is handled using a login endpoint that returns an access token.

## Technologies Used
- Postman
- JavaScript (for Postman tests)
- JSON (for API responses)
  
## Installation and Setup

1. Install Postman.
2. Clone this repository to your local machine.
3. Import the Postman collection provided in the repository.
4. Set up the environment variables for baseURL and accessToken in Postman.
   
## Postman Collection

The Postman collection is structured as follows:

1. Login and Authentication (POST): Authenticate and retrieve an access token.
2. Create a New Idea (POST): Create a new idea with a title and description.
3. List all Ideas (GET): Retrieve a list of all ideas.
4. Edit the Last Idea (PUT): Modify the last created idea.
5. Delete the Edited Idea (DELETE): Remove the last edited idea.
   
## Tested Endpoints
### Login and Authentication

- Method: POST
- URL: /api/User/Authentication
- Description: This endpoint authenticates the user and returns an access token.
- Tested Assertions:
     - Status code is 200.
     - The response body contains the email, password, and accessToken.
     - The access token is stored in a collection variable for further use.

pm.test("Code is 200", function () {
  pm.response.to.have.status(200);
});
pm.test("Response body has email, password, and accessToken", function() {
  const responseData = pm.response.json();
  pm.expect(responseData.email).not.to.be.empty;
  pm.expect(responseData.password).not.to.be.empty;
  pm.expect(responseData.accessToken).not.to.be.empty;
});
pm.collectionVariables.set("accessToken", pm.response.json().accessToken);

### Create a New Idea

- Method: POST
- URL: /api/Idea/Create
- Description: Creates a new idea with a title and description.
- Tested Assertions:
     - Status code is 201.
     - The response includes the created idea's ID and title.
       
### List all Ideas

- Method: GET
- URL: /api/Idea/List
- Description: Retrieves a list of all available ideas.
- Tested Assertions:
      - Status code is 200.
      - The response contains an array of ideas.
  
### Edit the Last Idea

- Method: PUT
- URL: /api/Idea/Edit
- Description: Edits the last created idea.
- Tested Assertions:
      - Status code is 200.
      - The response includes the updated idea's details.
  
### Delete the Edited Idea

- Method: DELETE
- URL: /api/Idea/Delete
- Description: Deletes the last edited idea.
- Tested Assertions:
     - Status code is 204 (No Content).
     - The idea is successfully removed.
       
### Running the Tests

1. Run the Postman collection in Postman.
2. Ensure that the accessToken is set correctly after running the login request.
3. Verify the results of the tests in the Postman console.
   
### License

This repository is licensed under the MIT License.

### Disclaimer

Please note that the Idea app/API tested in this project is the property of SoftUni, and this repository only contains my personal testing and automation scripts related to it.

