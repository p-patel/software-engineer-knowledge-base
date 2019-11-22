# Getting Started with TeamCity
https://app.pluralsight.com/library/courses/teamcity-getting-started/

## Setting Up TeamCity

### Server Agent Model
- TeamCity Architeture:
Server:
  Services:
    Server
    Agent - Build (scale-out agent build nodes)
    
### Windows Installation
- Above services are installed as Windows Services
- Agents
- TC requires a Data Directory, a db (e.g. MySQL, Postgres, SQL Server)
- `Get-Service TeamCity` lists TC server service
- `Get-Service TCBuildAgent` lists TC build agent service
- Check number of connected Agents in TC main navigation

### Linux and Mac Installation
...

### A docker-compose.yml for TeamCity
- Running TC in Docker containers (separate containers for TC Server and agents)

### Starting TeamCity Docker Containers
- Need to authorise unauthorised agents (when build agent is running in separate container to TC server)


### Configuring vs Consuming and User Accounts
- Consume: Projects, Changes, Agents, Build Queue sections
- Configure: Administration section
- User accounts options: Authentication | built-in authentication, Active Directory, LDAP, Windows Domain

## Creating Application Builds

### Anatomy of a Build
- Clone repo, compile, run unit tests, package (Compile, Testm, Package)

### Cloning the Sample Project
- Clone repo to a local workspace

### Installing Build Tools
- Git repo requires Maven to build app (install using brew/Chocolatey)
- Git required too

### Manually Compiilng an Application
- `mvn compile`

### Manually Testing an Application
- `mvn test`

### Manually Package an Application
- package to deploy or archive for historical purposes
- `mvn package` (generates `.war` file for Java applications)
- for Ruby (gem), .NET (zip/nuget), JS (bundle/minified file)

### Automating Builds
- easily track issues in a build back to a particular commit in the repo
- steps to automate: clone repo (in TC workspace), compile, test, package

### Creating a TeamCity Project and Build Configuration
- Workspace within the context of a build agent
- Create a project from a repo URL
- Build Configurations are a template of the build steps to be performed automatically
- Projects ("folders"), Build Configurations ("individual files")
- TC auto-detects build steps based on the connected repo! (selet desired steps)

### Detecting Build Tools






