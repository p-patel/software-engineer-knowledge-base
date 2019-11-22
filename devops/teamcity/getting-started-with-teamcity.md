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










