# Architecture Diagram
This diagram descripe the main components of the SIP application, and how these components interact with each other.

The core components is the SIP app that has the UI, mainly interact with the backend to perform its logics, sendand retrieve data.
Next we have the backend powerd by Supabase platform which perform diverce services, including:
1. Authentication Service: it perform authenticatio services such as: Sign up, Login and Resetting the password and insure a scure access to the user acccounts and data.
2. Logic: it perform the bussiness logic including the system boundery, the system behaviour and how the system should react.
3. Image/File Storage Service: Stores locally the app images and files.
4. Date Processing: Fetch the raw data and converted it to an structured form that is acceptable by the database.

Now moveing to the database service by PostgreSQL, which cover the following services:
1. Secure a persistent storage for the user data.
2. Define the main structure of the database (primary and forign keys, data types).
3. Send and fetch structured data from the backend.
4. Fetch the prediction results.

Next we have the AI model that will recive the CGM reading, carb inputs and any related information from the database and send the prediction results back to the database.

   

