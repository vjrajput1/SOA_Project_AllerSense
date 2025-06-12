# SOA_Project_AllerSense
Following is the detail regarding our project.
1. Use Case and Overall Project Scope
Use Case:
AllerSense will help users with food allergies detect potential allergens in packaged food using AI-powered image scanning and providing them the notification of allergens present or not.
Scope:
• Mobile app for Android and iOS using React Native
• AI-powered allergen detection through label scanning
• Personal Scan history
• Integration with external food APIs and custom ML models
• Cloud-based microservices and secure user management

2. Core Microservices and API Contracts
We are planning to implement the following microservices for the application:
1.	User Microservice
•	This microservice will mainly focus on user login and user preferences for the allergens. 
API Contracts for this microservice would be as follows:
1.	For User Registration:
•	Endpoint - /api/users/register
•	Method – POST
•	Request Parameters – 
i.	Email, Password, Preferences
•	Response Parameters – 
i.	UserId/Email, Message: Registration Successful.

2.	For User Login:
•	Endpoint - /api/users/login
•	Method – POST
•	Request Parameters – 
i.	Email, Password
•	Response Parameters – 
i.	Token, UserId/Email




3.	For User profile and preferences:
•	Endpoint - /api/users/:id
•	Method – GET
•	Response Parameters – 
i.	UserId/Email, Preferences

2.	Food Microservice (makes the caching and requests to FoodFactsAPI)
•	This microservice will mainly focus on sending requests to FoodFactsAPI and fetching the results from the Open-Source Food Database.
•	API Contracts for this microservice would be as follows:

1.	For Product Search:
•	Endpoint - /api/food/search
•	Method – GET
•	Request Parameters – 
•	Productname
•	Response Parameters – 
•	Results, which will include the product name and other info.

2.	For getting cached product information:
•	Endpoint - /api/food/:id
•	Method – GET
•	Response Parameters – 
•	ProductId, Name, Ingredients.

3.	For adding information to local cache:
•	Endpoint - /api/food/cache
•	Method – POST
•	Request Parameters – 
•	ProductId, Name, Ingredients
•	Response Parameters – 
•	Cache status.

3.	TensorFlow Microservices (for package prediction)
•	This microservice will focus on image scanning and predicting the correct food product based on the developed AI model.
•	API Contract for this microservice would be as follows:

1.	For predicting food product from image
•	Endpoint - /api/tensorflow/predict
•	Method – POST
•	Request Parameters – 
•	Scanned Image
•	Response Parameters – 
•	 Predicted ProductName, Confidence, Ingredients. 

4.	Monitoring / Analytics microservice (user interaction, observability)
•	This microservice will focus on monitoring and storing the recent scan history of the user.
•	API Contracts for this microservice would be as follows:

1.	For adding a record in the scan history:
•	Endpoint - /api/analytics/scan
•	Method – POST
•	Request Parameters:
•	UserId/Email, Productid, scan time
•	Response Parameters:
•	Status of record

2.	For fetching the user's scan history:
•	Endpoint - /api/analytics/user/:id
•	Method – GET
•	Response Parameters:
•	Product Name, allergens detected.

 
