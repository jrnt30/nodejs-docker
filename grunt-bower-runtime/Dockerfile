FROM jrnt30/nodejs-grunt-bower

# Set instructions on build.
ONBUILD ADD package.json /app/
ONBUILD RUN npm install
ONBUILD ADD bower.json /app/
ONBUILD ADD .bowerrc /app/
ONBUILD RUN bower install --allow-root
ONBUILD ADD . /app
ONBUILD RUN grunt build

# Define working directory.
WORKDIR /app

# Define default command.
CMD ["npm", "start"]

# Expose ports.
EXPOSE 8080
