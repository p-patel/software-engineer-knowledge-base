# CI Pipeline

## Overview
- VCS commit -> Restore dependencies -> Build -> Run Tests & Quality Checks -> Versioned Package Build Artifacts -> Publish to Repository (e.g. NuGet Server, TeamCity, Octopus Deploy, Artifactory)
- Support a multi-branch model (e.g. feature branches)

## CI Server & Build Agents
- Configure VCS, build triggers, build pipeline / build chain
- Use scripting like Cake to decouple build process from build server

### .NET Framework Build Agents
- Option A - MSBuild, Test Agent
- Option B - Visual Studio 
