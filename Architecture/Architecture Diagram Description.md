# Architecture Diagram
This diagram illustrates the main components of the SIP application and explains how they interact to provide a secure, intelligent, and responsive insulin management system.

At the center of the architecture is the SIP Application, which contains the user interface (UI) and serves as the primary interaction point for the user. The app communicates continuously with the backend to execute system logic, send user inputs, and retrieve processed data, predictions, and notifications. It acts as the presentation layer that displays glucose readings, insulin recommendations, alerts, and system status in a clear and user-friendly way.

## The backend is powered by the Supabase platform, which provides multiple core services essential for system operation:
* Authentication Service
This service handles all user authentication processes such as sign-up, login, and password reset. It ensures secure access to user accounts and protects sensitive medical and personal data by enforcing proper authorization and identity verification.

* Application Logic
This component implements the system’s business logic. It defines the system boundaries, governs system behavior, and determines how the application reacts to different inputs and events. It coordinates data flow between the database, AI model, insulin pump, and external APIs, ensuring that each component operates in a consistent and controlled manner.

* Image/File Storage Service
This service stores application-related images and files, such as profile pictures or medical documents, separately from structured database data. This improves scalability and keeps the database optimized for structured medical and system data.

* Data Processing
This component retrieves raw data from sensors and user inputs, cleans and validates it, and converts it into a structured format suitable for storage in the database. It ensures data consistency, accuracy, and compatibility with analytical and AI processing requirements.

## The system uses PostgreSQL as its main database service, which plays a critical role in data management:
* It provides secure and persistent storage for all user data, medical readings, predictions, and system logs.
* It defines the core database structure, including tables, primary and foreign keys, relationships, and data types.
* It supports sending and retrieving structured data between the backend and other system components.
* It stores and provides access to AI model prediction results so they can be used by the system logic and displayed in the SIP application.

## The AI Model
is responsible for intelligent decision support. It retrieves CGM readings, carbohydrate inputs, and other relevant medical and contextual information from the PostgreSQL database through the backend. These data are processed using predictive algorithms to estimate blood glucose trends and recommend appropriate insulin doses.
The generated prediction results are then stored back in the database. These results are used by the system logic to:
* Display insulin recommendations in the SIP application
* Support clinical and user decision-making
* Trigger alerts, warnings, or emergency actions when abnormal or dangerous conditions are detected

## The Insulin Pump Hardware Integration enables secure and controlled communication between the backend and the physical insulin pump device. Through dedicated communication interfaces:
* The backend sends insulin dose execution commands to the pump
* The pump responds with confirmation messages or error notifications
* All pump-related actions are logged in the database to ensure traceability, continuous monitoring, and safe system operation. This closed-loop interaction enhances system reliability and patient safety.

Finally, the system integrates with external API Services to enhance responsiveness and safety:
## Notification Service API
This service delivers real-time alerts and notifications to the user’s device based on system events and AI model outputs. It informs users about:
* High or low blood glucose levels
* Insulin dose recommendations
* Important system updates and warnings
* This ensures timely awareness and promotes proactive user action.

## Emergency Service API
This service acts as a critical safety layer and is activated only in high-risk situations. When dangerous glucose levels are detected or when the user fails to respond to repeated alerts, the system automatically triggers predefined emergency procedures. These may include:
* Sending urgent notifications to emergency contacts
* Notifying medical or emergency services
* Escalating system alerts to ensure rapid intervention
