# Look up what people usually use
FROM node:alpine 

WORKDIR /usr/app

COPY package.json .

RUN npm install

COPY . .

CMD ["npm", "run", "start"]
# can't run react container in -d (detached mode). Has to be -it mode.
# If you make a change to the source file, it won't be reflected on our localhost:3000 because the image that is already built still has the original code
# You would need to rebuild the image and then run a new container (i.e., give the container a new name). Quite cumbersome
# You can solve this solution using volumes. Volumes map the directory on our computer to the working directory of the container.Able to see changes in realtime
# When you run the container use -> -v (pwd):workdir of container -> e.g. /home/nisarg/Documents/My_Projects/Docker-Crash-Course/02-Working-with-Volumes/start:/usr/app
# The problem with this approach is that we haven't installed the node modules as the container does that. But then when we map the container loses the node modules
# A way around this is to use another volume -> anonymous volume -> -v /usr/app/node_modules -> this means leave the node modules alone
# sudo docker run -v /home/nisarg/Documents/My_Projects/Docker-Crash-Course/02-Working-with-Volumes/start:/usr/app -v /usr/app/node_modules --name react-container-with-volumes -it -p 3000:3000 react-app