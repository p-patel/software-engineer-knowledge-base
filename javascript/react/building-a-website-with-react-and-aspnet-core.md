# Building a Website with React and ASP.NET Core
https://app.pluralsight.com/courses/28d4cdc7-0756-46ca-be70-abef05ec970f/table-of-contents

## Course Overvieww
- Building a React app using Webpack
- Building a React app using `create-react-app` (CRA)
- Implementing REST calls
- Using Server Side Rendering (SSR)

## Introducing How To Build Connected React SPAs
### Learning React with ASP.NET Core as the Backend
- Build high-end, scalable, connected web apps
- Using REST architecture
- With a good development environment - automated testing (with no back-end dependency), consistent approach, producing reliable code

### 3 Techniques To Integrate React And ASP.NET Core
- React is not opionionated (unlike SPA frameworks such as Vue, Angular)
- 3 options:
  - Manual Webpack config
  - ASP.NET Core's React app template
  - Facebook's CRA tool
 - All above options are based on Webpack (module bundler) and json-server (fake REST server)
 
### Source Code On GitHub
- https://github.com/pkellner/pluralsight-course-react-aspnet-core
 
## Building a Custom Webpack Configuration for React and Core
### Introducing Custom Webpack Integration
- CRA does not support server-side rendering (SSR), a custom Webpack configuration is required
- Steps:
  - Create a JS bundle
  - Add React to bundle
  - Add react-router
  - Update to real-world site
  - Add SSR
  - Host/publish to ASP.NET Core

### Learn the JavaScript Build Tools
- Tools: Node.js, Webpack
- configure Webpack to generate a bundle from a source js file

### Learn To Work With webpack-dev-server
- setup a npm package for the dev site
- setup `\src` and `\public` directories for Webpack to bundle and webpack-dev-server to serve the site from
- Webpack should generate the bundle under `\public\js\`

### Bring in React and Create the First Component
- add Babel (to transpile JSX) and React to the site npm package
- client app js files moved to `ClientApp\` (Client.js and Hello.js)
- Hello.js is a React component used in Client.js, Client.js loads parent React component into HTML page
- webpack creates bundle, webpack-dev-server serves site

### Adding React Router to the App
- Multi-component app with routing
- add `/ClientApp/Components/common` dir
- install packages `react-router` and `react-router-dom`
- add `ClientApp/Components/common/FullPage.js` and use as the site's main component
- add `ClientApp/Components/common/Routes.js` to contain Switch component over all site routes
- add `historyApiFallback: true` to devServer config in `webpack.config.js`

### Updating the Example to a Conference Website
- create a website by creating multiple react routes and assets, sassAssets
- `FullPage` component wrapped with `<Router history={browserHistory}> </Router> in `Client.js`
- sass used to create CSS (covered in next module)

### Why You Are Not Done And Server Side Rendering
- Without SSR invalid routes will still return HTTP status code 200 (because BadRoute route is rendered client-side)
- Rendering server side first allows correct HTTP status code to be detected and returned. The rendered HTML can now also be sent to the client
- SSR Pro: client receives fully rendered page in a single request instead of client having to wait for JS to render the page client-side
- SSR Con: rendering compute transferred from client back to the server (increased cost/load)

### Splitting the WebPack Config into Two
- `webpack-dev-server` wraps express web server and serves the JS bundled by WebPack
- to provide SSR, Node.js will instead execute the bundled JS on the server using React and return the static rendered HTML
- this setup requires separate client and server WebPack configs
- use `webpack-merge` to refactor common WebPack config between the client and server configs
- the client WebPack config still creates the JS bundle as before (which is used on the client to render the root div tag in the blank HTML page sent to the client)

### Implementing Server Side Rendering and URL Validation
- 






