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
- The Go community and Core Go team addressed the two above issues separately circa. 2012-2016 before arriving at the Go Modules solution which was standardised in Go
- Read https://research.swtch.com/vgo-intro

## Overview of Modules
