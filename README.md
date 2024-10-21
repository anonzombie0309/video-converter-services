# Video Converter
Converting MP4 files into MP3 files using a Microservices Architecture

## Table of Contents

1. [Architecture](#architecture)
2. [Role of the Services](#role-of-the-services)
3. [Tech Stack](#tech-stack)

   
## Architecture

<p align="center">
  <img src="https://github.com/Indranil0603/video-converter-microservices/assets/95271465/9f83078a-42ba-4ae9-8516-0c39d6c23c75" width="700" title="Architecture" alt="Architecture">
</p>


## Role of Services
### 1. Auth Service :
The auth service is used for login it matches the email with the password and returns a JWT token that will be used for Authorization token for other services
### 2. Converter Service :
The converter service receives the mp4 files from the MP4 queue converts them to MP3 using moviepy library, stores them in the mongodb database, and sends the signal to the message queue after conversion in the MP3 queue.
### 3. Gateway Service :
The Gateway service serves as the point of contact for the client, all API calls are made through this service including /login, /upload, and /download.
### 4. Notification Service :
The Notification service receives a signal from the MP3 queue whenever a new file is converted it gets the ID for the MP3 file and sends a notification via email containing that ID.

## Tech Stack
Python ,Flask ,MongoDB ,PostgreSQL ,RabbitMQ ,kubernetes ,minikube

