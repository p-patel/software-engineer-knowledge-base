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
- Restart build agent to update ENV VARS after installing build tools on it `Restart-Service TCBuildAgent`
- Log files available on TC Server and build agents
- Set up Build Tasks within Build Configuration

### Running A Build
- Click 'Run' to run build
- Within build section there are two main areas: 'Build Configuration Home' and 'Edit Configuration Settings'

### The Build Log
- View Build Log to see the build steps activity on the Build Agent (logs collapsed into related sections)

### The Checkout Directory
- The checkout directory is a directory in the Build Agent's workspace
- Used when a build is run

### Cleaning Between Builds
- Avoid reusing build artefacts between builds
- Clean during build

### Capturing Packages as Artefacts
- Change Maven build step from 'compile' to 'package' to package Java app
- Packages can be archived for deployment and to keep an archive of builds
- In 'Build Configuration Settings' | 'General Settings', the 'Artifact paths' input can be used to specify paths to keep as artefacts from builds (can use wildcards to specify paths)
- Artefacts 'View' link is provided for each build to view the build artefacts (can also push artefacts out to Artefactory)

### Quizzery
1. Build error: 'Exit code 1'.  Check the build log for the particular build number to identify the issue
2. How do you view the current bulid status after it is run if not redirected automatically? Go to 'Build Configuration Home'
3. How do you go to the root of all projects in TeamCity? Click 'Projects'
4. On the project overview page, what represents the **build configuration**? The line under the project 'directory'
5. On the project overview page, what represents the **project**? The project 'directory'
6. On the project overview page, what represents the **build result**? The line number with the build number
7. On the project overview page, what represents the **output of a build**? The 'Artefacts' link

## Automating Builds for Fast Feedback

### Module Overview
- Robust automated build process has now been created.  But currently the build needs to be manually run each time
- Will automate running builds, look at reporting test results and providing notifications to avoid having to come into TeamCity unless there are errors.

### .NET Library Build Steps
- .NET Library build steps: Nuget Restore, MSBuild, NUnit tests, Nuget Pack

### Restoring NuGet Dependencies
- Create a new Build Configuration for the .NET library build
- Auto-detected Build Steps heuristics can be unreliable, e.g. may not detect the Nuget Restore step
- Add New Build Step runner type: 'NuGet Installer' (these are plugins).  Each type is a wrapper around a Command Line command
- Tools | Install Tool | NuGet.exe | Select a version (this installs NuGet on Build Agent and restarts the Build Agent) (use Install Tool to install tools required for Build Steps)
- Select version of NuGet.exe to use in the Build Step
- Set path to Solution File (used to detect Nuget packages to restore)
- Also see 'Show Advanced Options' to see more options for the Nuget Restore Build Step
- Save and run build
- In Build Result the Nuget Packages tab list the nuget package versions being used for all dependencies
- View Build Log tab to see the commands run during the Nuget Restore Build

### Adding a Second Build Step for MSBuild













