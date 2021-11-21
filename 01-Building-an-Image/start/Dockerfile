# Starting with a base image. 
# The base image we choose is dependent on the application we are running.
# Go to DockerHub to find images.
# Base image contains the basic utilities that we need such as Node, npm, git.
# What does :apline mean? It is just a version. The alpine version is the barebone version of node.
FROM node:alpine 


# Set the working directory so stuff copied in the next line isn't put into the root of the image.
# If we copy stuff into the root of the image and we have folders with the same name then we overwrite folders from the base images with the one we copied over.
# If /usr/app doesn't exist then it will generate it for you.
WORKDIR /usr/app

# This is a better way to do it so that npm install is only run if new dependencies are added, otherwise it just caches the next two steps which saves time.
COPY package.json .

# Install the dependencies/node modules.
# So no need to install node modules on our computer and then copy them over into the image.
# Can specify things we don't want copied over into the image through a .dockerignore file.
RUN npm install

# Copy current root working directory (the first dot) into the image's working directory.
COPY . .

# Run the start script.
CMD ["npm", "run","start"]

# Now build the image
# Make sure to be in the directory where the dockerfile is
# docker build -t express-app . (the . means the root/cwd where the docker file is)
# General form docker build -t <name of image> .
# After built, type docker images to see if the image is there. TAG means the versions of the images.
# If we delete this image and then rebuild it without changing the dockerfile or the code file, it is a lot quicker because every layer/step is already stored by Docker. I.e., it Caches it.
# Running a container -> docker run <image name>
# To know what containers are running? -> docker ps
# To remove the docker container docker rm <image name>
# You can detach the container from the terminal using -d flag -> docker run -d express-app
# Can also give the container a name -> docker run --name <name of container> <name of image>
# Two ways to stop a container -> docker stop <container name or id> or docker kill <container-name of id>
# docker stops just has an extra clean up process compared to docker kill
# docker start <container name or id>
# The app is running on port 3333 but if you go to it, it won't be there because it is running inside of the container
# Therefore, we need to map the containers port to our computers port
# docker run -d --name express-container -p 3333:3333 express-app (first port is our machine, second port is container's port)
