https://app.pluralsight.com/library/courses/exploring-go-modules

# Introduction and Overview
## Introduction
Course will cover:
- Introduction to modules in Go
- Standard workflow and tools
- Managing dependency versions
- Advanced scenarios and tools

## Goals of the Module System
- Keep existing strengths of Go Workspaces:
  - Easy dependency resolution with `go get`
  - Simple build process with all dependencies being located in a single location with the Go Workspace
- Address Weaknesses
  - Manage versioning of application and dependencies (inc. application API and dependencies API)
  - Vendoring of dependencies and ensuring reproducible builds with specific versions of dependencies

## History of Go Project Management
- The Go community and Core Go team addressed the two above issues separately circa. 2012-2016 before arriving at the Go Modules solution which was standardised in Go. It was based on the `dep` tool developed by the community in 2016.
- Read https://research.swtch.com/vgo-intro

## Overview of Modules
- A modules is one more related packages. Before this we had packages in the Go workspace and sub-packages within these packages
- A module has a go.mod file
- A module is versioned
- Go modules use semantic versioning
- Dependent libraries are kept in a cache
- Dependency integrity checks can be done via checksums

# Creating and Maintaining Modules
## Initialising a Module
- `go mod init <module/identifier/name>` (see `go help mod` for more info)
- `go build` works the same as it does with Go Workspaces

## Retrieving Dependencies
- use `go get -u github.com/gorilla/mux` which will update `go.mod` and create `go.sum` file
- `go get` includes support for specifying module version
- imported modules are not created within our project directory structure.  Go downloads and caches dependencies outside of our project's directory
- `// indirect` dependencies are modules that are not directly used within our module

## Listing Dependencies
- `go list`, `go list all`, `go list -m all`
- `go list -m -versions github.com/gorilla/mux` lists all available versions of a module

## Verifying Dependencies
- `go mod verify` (uses checksum from go.sum)
- go downloads and caches modules into Go workspace at `go/pkg/mod/`
- NB. `go build` will still run successfully when `go mod verify` fails

## Removinng Unused Dependencies
- `go build` will NOT remove unused module dependencies
- use `go mod tidy` to remove unused module dependencies

## Summary
- Continue to use existing tools which have been updated to support modules

# Advanced Module Management Tools
## Introduction
- Uses strict Semantic versioning

## Review of Semantic Versions
- `v1.5.3-pre1`
- `v` version prefix (required)
- `1` Major revision (likely to break backward compatibility)
- `5` Minor revision (new features, doesn't break backward compatibility)
- `3` Patch (bug fixes, no new features and doesn't break backward compatibility)
- `pre1` Pre-release (text is arbitrary but alphabetically ordered)

## Module Versioning Rules
- Three sets of rules:
  - Version 1 and earlier
  - Version 2+
  - Unversioned modules (modules that do not adopt Semantic Versionining)

## Versioning Rules: v1 and Earlier
- No promise of backward compatibility prior to v1.0.0
- Version precedence determined by major, minor then patch versions

## Versioning Rules: v2 and Beyond
- Backward compatibility should be preserved within a major version from v1.0.0
- Each major version has unique import path
- `import github.com/gorilla/mux/v2`

## Demo: Versioning Rules
- Demo using rsc.io/quote





