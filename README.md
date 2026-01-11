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

## Architectural Diagram

![Architecture Diagram](Diagram.jpeg)

AWS Amplify
provides a Git-based CI/CD workflow that allows you to build, deploy, and host web applications or static sites with serverless backends.
It automatically detects the build settings for both the frontend and any serverless backend resources when connected to a Git repository. With each code commit, Amplify redeploys updates automatically.
In this section, you'll create a new React application for your bucket list tracker, push it to a GitHub repository, and connect it to AWS Amplify for deployment.

## Create a React App using Vite

```bash
npm create vite@latest bucketlistapp -- --template react
cd bucketlistapp
npm install
npm run dev
```

Local development server runs at: http://localhost:5173/ (address may vary)

![React App Screenshot](ReactAPP.jpeg)

## Deploy the React App to AWS Amplify
https://main.dfnnoiwwumul6.amplifyapp.com/ (address may vary)

Setup AWS Amplify Backend
With Amplify, you can set up authentication, data storage, and file storage with a unified developer experience, which will allow users to manage their bucket lists.
1.authentication
By default, your authentication resource is configured in the bucketlistapp/amplify/auth/resource.ts
2.data storage
update bucketlistapp/amplify/data/resource.ts file, which will define a model for the bucket list items, ensuring that only the owner can access their data.
In this schema:
Each bucket list item includes a title, description, and a completed status.
The authorization rule ensures that only the user who created the item can access it.
3.file storage
Create a new folder called storage inside the bucketlistapp/amplify folder, and inside that, create a new file named resource.ts.
This storage configuration ensures that only the person who uploads the image can access it. The entity_id will be replaced with the user’s identifier during file uploads, restricting access to the file.
4.update amplify/backend.ts file 
This ensures that all the backend resources (auth, data, and storage) are properly configured and linked.
5.Deploy the Amplify Backend in a Cloud Sandbox
This command starts a Cloud sandbox, which is an isolated development environment connected to AWS Cloud resources to rapidly build, test, and iterate
npx ampx sandbox
When complete, you'll see: "Sandbox deployed successfully"
The amplify_outputs.json file will appear in your bucketlistapp folder
Keep the sandbox terminal running while developing

Connect Frontend and Backend
In this task, you will build the frontend of your bucket list tracker app and connect it to the cloud backend you have already set up.

You will use AWS Amplify’s UI component library to create a complete user authentication flow and implement the ability to create, update, and delete bucket list items.

Additionally, you will create the frontend of the bucket list tracker, where users can add, update, and delete items on their bucket list. They will also be able to upload images associated with each item.
1.Install Amplify Libraries
npm install aws-amplify @aws-amplify/ui-react
These libraries include the client-side APIs to connect your app's frontend to the backend services and the UI components for authentication.

2.UI Setup and Styling
2.1update bucketlistapp/src/index.css
This will set the layout and styles for the bucket list UI
2.2update bucketlistapp/src/App.jsx
This will set the content for the bucket list UI

3.Launch the App Locally
3.1npm run dev
3.2Open the local host link http://localhost:5173/ (address may vary)
3.3Choose the Create Account tab and use the authentication flow to sign up by entering your email and password. Then, create your account.

4.Test
Bucket List Item: "Visit Paris"
Description: "Rideau Canal"
Upload an image (JPEG)

AWS workflow
Step 1 - Database Storage (DynamoDB)
Item metadata (title, description, image filename) saved to DynamoDB via AppSync GraphQL API
Step 2 - File Storage (S3)
Image uploaded to S3 bucket via Amplify Storage
Path: media/{your-user-id}/{filename}
Only you can access your images (owner authorization)
Step 3 - Display
App fetches your items from DynamoDB
Generates secure URLs for images from S3
Displays all your bucket list items with images