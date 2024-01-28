### Docker Image

1. Clone the GitHub repository:

            git clone https://github.com/docker/getting-started-app.git

2. Change the path to the main directory:

            cd getting-started-app

3. Create Dockerfile

            type nul > Dockerfile

4. Using a text editor or code editor, add the following contents to the Dockerfile (Must Be In Order:

            # syntax=docker/dockerfile:1
            
            FROM node:18-alpine
            WORKDIR /app
            COPY . .
            RUN yarn install --production
            CMD ["node", "src/index.js"]
            EXPOSE 3000

5. Build the image

            docker build -t getting-started .

6. Run your container using the docker run command and specify the name of the image you just created:

            docker run -dp 127.0.0.1:3000:3000 getting-started

7. Run the following docker ps command in a terminal to list your containers:

            docker ps



### Update the application

When we update anything in the application, we have to create another image.                                                                                                                                                                                    

1. Change something in the app's code                                                                                                                                                                                                                        

2. Build your updated version of the image, using the docker build command:

            docker build -t getting-started .

3. Start a new container using the updated code:

            docker run -dp 127.0.0.1:3000:3000 getting-started

During this, we will have an error because we already have a container with same name and allocated to same port(3000)                                                                                                                        


### Remove the old container

We have to stop the container if it is still running.                                                                                                                                     

1. Get the ID of the container by using the docker ps command:

            docker ps
2. Use the docker stop command to stop the container. Replace <the-container-id> with the ID from docker ps:

            docker stop <the-container-id>

3. Once the container has stopped, you can remove it by using the docker rm command:

            docker rm <the-container-id>

4. Now, start your updated app using the docker run command:

            docker run -dp 127.0.0.1:3000:3000 getting-started

