# jrnt30/nodejs-grunt-bower-runtime

[`jrnt30/nodejs-grunt-bower-runtime`](https://index.docker.io/u/jrnt30/nodejs-grunt-bower-runtime) is a [docker](https://docker.io) base image for easily running [nodejs](https://nodejs.org) application.

It can automatically bundle a nodejs application with its dependencies and set the default entrypoint with no additional Dockerfile instructions.

It is based on [`google/nodejs`](https://index.docker.io/u/google/nodejs) base image.

## Usage

- Create a Dockerfile in your nodejs application directory with the following content:

        FROM jrnt30/nodejs-grunt-bower-runtime

- Run the following command in your application directory:

        docker build -t app .

## Notes

The image assumes that your application:

- has a file named [`package.json`](https://www.npmjs.org/doc/json.html) listing its dependencies.
- has a file named [`bower.json`](http://bower.io/docs/creating-packages/)
- has a file named [`.bowerrc`](http://bower.io/docs/config/)
- has a [`Gruntfile`](http://gruntjs.com/sample-gruntfile) with a [`build task`](http://gruntjs.com/creating-tasks)
- supports `npm install` via the  `package.json` attribute: `"scripts": {"start": "node <entrypoint_script_js>"}`
- listens on port `8080`

### Example

`package.json`

    {
      "name": "hello-world",
      "description": "hello world test app",
      "version": "0.0.1",
      "private": true,
      "dependencies": {
        "express": "3.x"
      },
      "scripts": {"start": "node app.js"}
    }

When building your application docker image, `ONBUILD` triggers fetch the dependencies listed in `package.json`, `bower.json` and cache them appropriatly, after which Grunt build will be called.
