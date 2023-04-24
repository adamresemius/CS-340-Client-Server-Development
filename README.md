Animal Shelter Database Management System

Introduction
This Python program implements a simple Animal Shelter Database Management System with the Dash Framework from Plotly to create a UI with MongoDB as the backend database. Database functions include CRUD which stands for create, read, update, and delete documents (records) in the database. This DBMS is designed to help Grazioso Salvare, an international rescue-animal training company, identify The program allows users to authenticate into and categorize dogs from animal shelters in the Austin, Texas region for search-and-rescue training. This README file provides an overview of the project and instructions for setting up and running the database.

Prerequisites
Before running the program, make sure you have the following prerequisites:
Python 3 installed
pymongo and bson Python modules installed
You can install the required modules using the following commands:

 ![image](https://user-images.githubusercontent.com/103894466/233904556-a41da507-e30c-4984-9934-c20d649c0474.png)
![image](https://user-images.githubusercontent.com/103894466/233904629-f75798b3-9d17-46bd-9793-fc410a4720f7.png)

 
Please follow the documentation on installing Dash modules at ‘https://dash.plotly.com/installation’ 

AnimalShelter Class
This class includes an authentication mechanism to connect to the MongoDB database. The constructor (init method) takes two parameters: username and password. These credentials are used to authenticate the connection to the database using MongoClient from the PyMongo library. The connection string includes the username and password, which are passed as arguments to the MongoClient constructor.
create(data): This method creates a new document in the MongoDB database with the provided data. The data parameter should be a dictionary containing the information for the new document. If the creation is successful, the method returns True. Otherwise, it raises an exception.
read(data): This method searches for documents in the MongoDB database that match the provided data. The data parameter should be a dictionary containing the search criteria. If documents are found, the method returns a list of documents. Otherwise, it raises an exception.
update(query, data): This method updates documents in the MongoDB database that match the provided query with the provided data. The query parameter should be a dictionary containing the search criteria for the documents to be updated, and the data parameter should be a dictionary containing the new data to be updated. The method returns the result of the update operation, which may include information about the number of documents updated. If no documents are found to update, the method raises an exception.
delete(query): This method deletes documents in the MongoDB database that match the provided query. The query parameter should be a dictionary containing the search criteria for the documents to be deleted. If documents are deleted, the method returns True. If no documents are found to delete, the method returns False. 
Note: All methods in the AnimalShelter class are designed to raise an exception if an error occurs during the database operation, such as connection errors or invalid data formats. Exception handling should be implemented in the calling code to handle potential errors gracefully. The AnimalShelter class likely requires a connection to a MongoDB database, and appropriate configurations for the connection (e.g., hostname, port, database name, authentication credentials) should be provided in order for the class to interact with the database correctly. Further documentation or comments in the code may provide additional information on how to configure and set up the AnimalShelter class for use. Please refer to the AnimalShelter.py file for the specific implementation details.
Backend Interaction
Run the main.py file in your Python environment.


Enter your database username and password when prompted for authentication.
 
 ![image](https://user-images.githubusercontent.com/103894466/233904777-ca488274-eb4a-47a7-bef2-97e93e64b06d.png)


Once authenticated you can choose from the following options within the menu. This is not case sensitive. 

![image](https://user-images.githubusercontent.com/103894466/233904797-5b43f05a-c57a-4fe5-b4f7-8518aca9720a.png)


Press 'C' to create a document: Enter a valid JSON string to create a new document in the database.

![image](https://user-images.githubusercontent.com/103894466/233904813-c3840470-88e4-4e48-be69-f0d44fc66756.png)


Press 'R' to read a document: Enter a valid JSON string to search for documents in the database.
 
 ![image](https://user-images.githubusercontent.com/103894466/233904860-75f8d5f9-5352-43a8-a950-c679e0a4d416.png)


Press 'U' to update a document: Enter a valid JSON string for querying documents to be updated, and another JSON string with the data to update.
 
![image](https://user-images.githubusercontent.com/103894466/233905020-863a07b3-8c70-4bc9-b404-16a3d270d41a.png)


Press 'D' to delete a document: Enter a valid JSON string for querying documents to be deleted.

![image](https://user-images.githubusercontent.com/103894466/233905037-b10970c7-26f2-4659-9836-2c141b8870cf.png)
 

Press 'Q' to quit the program: Confirm your choice to quit or continue using the program.
 
 ![image](https://user-images.githubusercontent.com/103894466/233904933-52e97c40-e99a-4ec7-b2dc-4634b61b29df.png)


The program will display the result of each operation, whether it was successful or not.
Challenges Encountered
Converting User Input to JSON: One challenge encountered was converting user input into JSON format, as the data needed to be stored in the MongoDB database as JSON. This required using the built-in json module in Python to serialize the user input into JSON format before storing it in the database.
Setting up Authentication for the Database: Another challenge encountered was setting up authentication for the MongoDB database when connecting to it from localhost. This required passing the username and password as parameters to the MongoClient constructor, and properly configuring the authentication credentials to connect to the database securely.
Error Testing
Testing non-JSON query input
Description: Testing what will happen with each function when the user enters a non-JSON query into the terminal.
 
![image](https://user-images.githubusercontent.com/103894466/233905147-1b866cb6-9d3a-47af-b977-d8fb592e9125.png)
![image](https://user-images.githubusercontent.com/103894466/233905164-c00033c2-b213-419f-87d0-f93de642ba1b.png)


Testing create function with no input
Description: Checking to see what happens when passing nothing through the create function. The result was that a document was created, which was unexpected. An exception should have been thrown. This will need patching.

![image](https://user-images.githubusercontent.com/103894466/233905229-08727b71-fb38-4078-bf24-c86adb9cbe76.png)

 
Testing read function with non-existent query
Description: Attempting to read a document that doesn't exist. While this shows that the operation was successful with no read result between [], I would like to implement some logic to inform the user that there weren't any documents found for the searched query.
 
 ![image](https://user-images.githubusercontent.com/103894466/233905264-fc492378-38c3-47ef-a692-e3d22c94605c.png)


Testing update function with non-existent document
Description: Attempting to update a document that doesn't exist. Although it seems like something was updated, when searched, the results show nothing. I will create an error code for this, stating that no document was found to update, and prompt the user to create a document with the specified criteria.
 
 ![image](https://user-images.githubusercontent.com/103894466/233905286-e19e1065-0155-4efb-9c98-34e7b3a2d503.png)

Testing delete function with non-existent document
Description: Attempting to delete a document that doesn't exist.
 
 ![image](https://user-images.githubusercontent.com/103894466/233905332-3c2aa7a1-8309-4939-bfec-9e11c69b620b.png)


Testing authentication without proper credentials
Description: User is able to see the menu, but when they try to use a CRUD function, they get a traceback error. This is likely due to lack of account privileges to interact with the database. I will need to create a more proper authentication system that informs the user if their credentials are invalid.
 
 ![image](https://user-images.githubusercontent.com/103894466/233905365-ac20da96-76f0-492c-8035-dfa8784e18f1.png)


Frontend Interaction
	The Dash framework from Plotly is used to create the user interface (UI) for the Animal Shelter Database Management System. The UI includes a Data Table and a map. The Data Table displays the records from the MongoDB database and includes filter buttons for the user to sort records by the type of animal rescue. When the user selects a filter, the Data Table is updated with the relevant records. The user can also delete records by selecting the rows and clicking the delete button. The map displays the locations of the animal shelters in the Austin, Texas region. Markers on the map are updated based on the filters selected by the user in the Data Table. The UI is designed to help Grazioso Salvare, an international rescue-animal training company, categorize dogs from animal shelters in the Austin, Texas region for search-and-rescue training.
 
 ![image](https://user-images.githubusercontent.com/103894466/233905392-1ffaef23-1f7a-42f9-aa45-cadcb309b22d.png)


To use the dashboard, simply change the filter dropdown to the suggested rescue type and the dashboard will update to show the documents for that type of rescue animal. 
The dashboard layout is designed to be simple and intuitive, with a clear focus on animal rescue types.  The app layout includes a section for Rescue Filters, which provides users with the option to select from Water Rescue, Mountain or Wilderness Rescue, Disaster Rescue or Individual Tracking, and Reset.
 
![image](https://user-images.githubusercontent.com/103894466/233905500-2e5561ec-860a-4286-abe4-d40631329525.png)

The map displays the locations of the animal shelters in the Austin, Texas region. Markers on the map are updated based on the filters selected by the user in the Data Table. The map is interactive, allowing the user to zoom in and out and pan around the map. The map is especially useful for visualizing the distribution of shelters in the region and identifying those that are in areas that are most convenient for the rescue team.
The provided screenshot displays the Mountain or Wilderness Rescue dogs.
 
![image](https://user-images.githubusercontent.com/103894466/233905572-4b2bc6e4-8dd0-4450-b018-c37c5ea8f758.png)


The pie chart is an added effective way to visualize the distribution of dog breeds in the dataset, as it allows the user to quickly see the most common breeds and how many there are. This information can be useful for Grazioso Salvare for search-and-rescue training.
 
 ![image](https://user-images.githubusercontent.com/103894466/233905611-0802afd6-b9a1-4801-b697-a2a4cb028d60.png)

Summary
The Animal Shelter Database Management System is a Python program that uses MongoDB as the backend database. It is designed to help Grazioso Salvare, an international rescue-animal training company, identify and categorize dogs from animal shelters in Austin, Texas for search-and-rescue training. The backend script allows users to authenticate into the database and use CRUD functions to create, read, update, and delete documents in the database. The AnimalShelter class in the program includes methods for handling these operations, such as create, read, update, and delete. The program requires prerequisites such as Python 3 and pymongo and bson Python modules to be installed. Users can run the program, authenticate with their database credentials, and choose from options in the menu to perform various operations. Challenges encountered during development included converting user input to JSON format and setting up authentication for the MongoDB database. Proper exception handling and configuration of the AnimalShelter class are important for the correct usage of the program. This Animal Shelter Database Management System provides a simple yet effective solution for managing animal shelter data for search-and-rescue training. Please refer to the AnimalShelter.py file for specific implementation details.
	Users that are unaware of how to use Database sets can easily visualize the information provided to them through the interactive dashboard made with Dash Framework. As shown above they can filter through the rescue types to quickly find animal shelters with dogs per the rescue type selected. If they would like to browse manually, there is another filter option that allows them to type in text and the table and map will update accordingly.  

