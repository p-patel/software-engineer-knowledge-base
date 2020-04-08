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
 
