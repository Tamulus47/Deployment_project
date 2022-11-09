# about

- this project deploy backend api and frontend app on AWS using circleci and github to automate the process.
- frontend application link: http://frontendapp512.s3-website-us-east-1.amazonaws.com

### Built With

- [Angular](https://angular.io/)
- [Node](https://nodejs.org)
- [Express](https://expressjs.com/)

### Dependencies

- Node v14.15.1 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version
- npm 6.14.8 (LTS) or more recent, Yarn can work but was not tested for this project
- AWS CLI v2, v1 can work but was not tested for this project
- A RDS database running Postgres.
- A S3 bucket for hosting uploaded pictures.

### Installation

Provision the necessary AWS services needed for running the application:

1. In AWS, provision a publicly available RDS database running Postgres. <Place holder for link to classroom article>
2. In AWS, provision a s3 bucket for hosting the uploaded files. <Place holder for tlink to classroom article>
3. Export the ENV variables needed or use a package like [dotnev](https://www.npmjs.com/package/dotenv)/.
4. From the root of the repo, navigate udagram-api folder `cd starter/udagram-api` to install the node_modules `npm install`. After installation is done start the api in dev mode with `npm run dev`.
5. Without closing the terminal in step 1, navigate to the udagram-frontend `cd starter/udagram-frontend` to intall the node_modules `npm install`. After installation is done start the api in dev mode with `npm run start`.

### Testing

This project contains two different test suite: unit tests and End-To-End tests(e2e). Follow these steps to run the tests.

1. `cd starter/udagram-frontend`
2. `npm run test`
- Unit tests are using the Jasmine Framework.
3. `npm run e2e`
- The e2e tests are using Protractor and Jasmine.

### pipeline process

circleci start with build and in this step the following happens:
1. setup work environment.
2. prepare environment variables.
3. install node.js.
4. checkout files from github.
5. run `npm run frontend:install` & `npm run api:install` to install dependencies for frontend and backend.
6. run `npm run frontend:lint` to check code fromat.
7. run `npm run frontend:build` & `npm run api:build` to build js files for frontend and backend.
then waiting for approve and accordingly start with deploy step and the following happens:
1. setup elastic beanstalk cli.
2. install aws cli.
3. configure aws profile from environment variables.
4. checkout api files from github.
5. run `npm run deploy` to upload files to elastic beanstalk.