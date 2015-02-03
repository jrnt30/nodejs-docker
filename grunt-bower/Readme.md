# jrnt30/nodejs-grunt-bower

[`jrnt30/nodejs-grunt-bower`](https://index.docker.io/u/jrnt30/grunt-bower) is a [docker](https://docker.io) base image that bundles the latest version of [nodejs](https://nodejs.org) and [npm](https://npmjs.org) installed from [nodejs.org](http://nodejs.org/download/). 

In addition, it globally installs [`bower`](http://bower.io/), [`grunt-cli`](http://gruntjs.com/) and PhantomJS dependencies. 

It serves as a base for the [`jrnt30/grunt-bower-runtime`](https://index.docker.io/u/jrnt30/nodejs-grunt-bower-runtime) image.

## Usage

- Create a Dockerfile in your nodejs application directory with the following content:

        FROM jrnt30/nodejs-grunt-bower
        
        WORKDIR /app
        ADD package.json /app/
        RUN npm install
        ADD . /app
        
        CMD []
        ENTRYPOINT ["/nodejs/bin/npm", "start"]

- Run the following command in your application directory:

        docker build -t my/app .

