# set the base image to create the image for react app
FROM node:20-alpine


# Create user named 'app'
RUN addgroup app && adduser -S -G app app

# set the user 'App'
USER app

# Lahat ng files at commands ay mangyayari sa folder na /app
WORKDIR /app

# copy package.json and package-lock.json to the working directory
# This is done before copying the rest of the files to take advantage of Docker’s cache
# If the package.json and package-lock.json files haven’t changed, Docker will use the cached dependencies
COPY package*.json ./

# Kailangan ng admin powers para mag-ayos ng permissions
USER root

# Siguraduhin natin na may access si app user sa folder niya
RUN chown -R app:app .

# Safe na ulit tumakbo bilang normal user
USER app

# install dependencies
RUN npm install

# copy the rest of the files to the working directory
COPY . .

# expose port 5173 to tell Docker that the container listens on the specified network ports at runtime
EXPOSE 5173

# command to run the app
CMD npm run dev