# UdaTube

## Description
This project is based on YouTube - a website to upload and sharing videos.

## Features
1. Login / Logout using Auth0.
2. Create video using MP4 file and PNG file as thumbnail.
3. Update video.
4. Delete video.
5. Update profile (change avatar, change username).
6. Subscribe / Unsubscribe to other users.
7. Search videos.
8. Search users.
9. Watch video.
10. React to a video (like, dislike).
11. Comment to a video.
12. View other comments.
13. View videos of a user

## Demo

Website: https://udatube-udacity.web.app/

API endpoint: https://m9ibeaaw33.execute-api.us-east-1.amazonaws.com/dev

## Setup

Development kit:
* AWS CLI with default profile has been setup.
* NPM/Yarn:
  * NPM version: 8.3.1
  * Yarn version: 1.22.19
* Serverless framework. This project is using version as below:
  * Framework Core: 3.22.0
  * Plugin: 6.2.2
  * SDK: 4.3.2

The root folder of the project contains 2 links to 2 repositories of frontend folder and backend folder

### Backend

Folder: udatube/

The backend for this project is using Serverless framework, monitored by AWS Cloudwatch and AWS Xray.

Project structure:

* **serverless.ts**: (like serverless.yaml) construct the setup like DynamoDB tables structure, roles, functions, envs, etc.
* **roles**: contains role for each function, separated in corresponding files to track easier.
* **libs**: some usefull functions like resize image using Jimp package, middify functions
* **errors**: contain single file Errors.ts to list every possible errors to catch alongside with status code when calling api
* **functions**: each function is separated in corresponding folder, including index.ts file to declare function handler, role name, function name, event handler; handler.ts contains the code for function
* **businessLayer**: business layer, divided into 3 main features: user, comment and video. This layer recieves raw information from function handler to check for valid data input, existed resource, valid access to resource and other logic.
* **dataLayer**: data layer, like business layer, divided into 3 main features: user, comment and video. This layer recieves data from business layer and save to AWS resource like DynamoDB, S3. Details information can be found in file README.md in udatube folder.

Each step when calling the api will be logged using AWS CloudWatch Logs and traced by AWS X-Ray.

Setup: run yarn install. After that, run serverless deploy to deploy.


### Frontend

Folder: udatube-client/

The frontend for this project is using React with MUI for the UI and React Context API to manage state.

Setup: run yarn install. After that, run yarn start to start local server. Open browser at localhost:3000
