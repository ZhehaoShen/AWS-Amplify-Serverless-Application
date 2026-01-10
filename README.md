Overview of Project ☁️
The final project is to deploy a 'Bucket List Tracker' application on AWS Amplify. It will take longer than the others to build out, but by the end of it, you will learn a lot about how to create serverless applications.

Steps to be performed 👩‍💻
In the next few lessons, we'll be going through the following steps.

Develop a bucket list tracker application in React
Initialize a Github repository and connect it to your local repository. Host the frontend on Amplify Hosting
Use Amplify Studio/ Amplify CLI and integrate Amplify Authentication providing user authentication for Login/Signup
Create a AWS AppSync service for building and managing a GraphQL API, and a GraphQL schema for DynamoDB service integration
Deploy the backend on AWS Amplify to handle data storage and server-side logic
Services Used 🛠
AWS Amplify: Deployment of frontend and backend services.
AWS AppSync: Simplifies building and managing scalable GraphQL APIs.
GraphQL API: Allows clients to request only the data they need. [API & Schema]
DynamoDB: DynamoDB for storing and managing bucket list items.[Database]
S3 bucket: For storage of user images. [Storage]

Architectural Diagram


AWS Amplify
provides a Git-based CI/CD workflow that allows you to build, deploy, and host web applications or static sites with serverless backends.
It automatically detects the build settings for both the frontend and any serverless backend resources when connected to a Git repository. With each code commit, Amplify redeploys updates automatically.
In this section, you'll create a new React application for your bucket list tracker, push it to a GitHub repository, and connect it to AWS Amplify for deployment.

Create a React App using Vite

http://localhost:5173/ (address varies)

