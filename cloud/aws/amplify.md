# Amplify

## Docs
- https://docs.amplify.aws/start/q/integration/js/
- https://docs.amplify.aws/cli/

## Managing team access
- https://docs.amplify.aws/console/adminui/access-management/

## Setup
- service role
  - https://docs.aws.amazon.com/amplify/latest/userguide/how-to-service-role-amplify-console.html

## Multiple front-ends
- https://docs.amplify.aws/cli/teams/multi-frontend/#workflow
- https://dev.to/norrischebl/multiple-frontends-with-aws-amplify-2p4f
- https://dev.to/applification/multiple-frontends-with-amplify-console-3nnj
- https://docs.aws.amazon.com/amplify/latest/userguide/reuse-backends.html
- https://youtu.be/2mqiZ7yqfLc

## React
- https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/
  - https://docs.amplify.aws/cli/start/install/#configure-the-amplify-cli

### Amplify Prebuild UI Components

### Amplify Native Libraries
- ...

## React Native

### Amplify Prebuild UI Components

### Amplify Native Libraries
- https://docs.amplify.aws/start/getting-started/setup/q/integration/react-native/#install-amplify-libraries
- https://docs.amplify.aws/start/q/integration/react/
- storage
  - https://docs.amplify.aws/lib/storage/getting-started/q/platform/android/


## Postgres DB
- https://stackoverflow.com/a/69624650
  - https://aws.amazon.com/blogs/mobile/appsync-microservices/
- Connect db to Amplify Content Management

## Framework Features

## Multiple Environments
- `amplify env ...`

## Auth
- Probably the best auth integration for Cognito
- https://blog.kylegalbraith.com/2020/03/31/customizing-the-aws-amplify-authentication-ui-with-your-own-react-components/
- Restrict api endpoints to authenticated users in a group?
  - https://docs.amplify.aws/cli/auth/groups/
  - https://docs.amplify.aws/console/auth/user-management/

### Storage
- offline/online sync

### Data Modelling
- https://docs.amplify.aws/console/data/data-model/

### AppSync deep-dive
- GraphQL API - connect any data source

### Data Management
- https://docs.amplify.aws/console/data/content-management/
- Content Manager is only supports the Amplify DataStore (not Amplify GraphQL API)
  - https://docs.amplify.aws/console/data/data-model/#limitations

### REST API
- https://docs.amplify.aws/cli/restapi/restapi/

### GraphQL API
- https://graphql.org/learn/

### Amplify function (serverless)
- https://medium.com/a-cloud-guru/serverless-functions-in-depth-507439b4be88
- https://docs.amplify.aws/cli/function/
  - use as a datasource in your GraphQL API using the @function directive
- aws-serverless-express
  - https://stackoverflow.com/questions/74329087/using-serverless-deployment-to-lambda-with-es6-node-js-v16
  - https://stackoverflow.com/questions/66676555/nodejs-14-x-native-aws-lambda-import-export-support
- use Webpack, Babel
- ES6 lambda functions
  - https://stackoverflow.com/a/45115440
  - https://sst.dev/chapters/add-support-for-es6-and-typescript.html
  - https://stackoverflow.com/questions/68808998/cannot-use-es6-on-aws-lambda-function-how-to-import-es6-module-within-lambda
- use TypeScript
  - https://medium.com/@jolodev/how-to-add-fancy-to-your-amplify-project-b13bbe13d61d
  - https://vdelacou.medium.com/how-to-use-typescript-with-aws-amplify-function-d3e271b11d01
  - https://stackoverflow.com/a/64762499
  - https://www.split.io/blog/building-a-serverless-express-and-typescript-application-with-aws-lambda/
- Common code structure
  - https://www.carlwillimott.com/quick-tips-when-working-with-lambda-in-aws-amplify/
  - yarn
    - https://github.com/aws-amplify/amplify-cli/issues/1696
    - https://www.digitalocean.com/community/tutorials/js-yarn-package-manager-quick-intro
  - layers
    - https://www.freecodecamp.org/news/how-to-reuse-packages-with-aws-lambda-functions-using-amplify/
- Env Vars
  - https://docs.amplify.aws/cli/function/env-vars/
- Secrets
  - https://docs.amplify.aws/cli/function/secrets/
