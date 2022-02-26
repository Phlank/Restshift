# Restshift <!-- omit in toc -->

- [Purpose](#purpose)
- [Milestones](#milestones)
  - [OpenAPI milestones](#openapi-milestones)
  - [Mapping milestones](#mapping-milestones)
  - [Authentication milestones](#authentication-milestones)
  - [Testing](#testing)
  - [Later goals](#later-goals)
- [Anticipated tech stack](#anticipated-tech-stack)
- [Challenges](#challenges)

## Purpose

Provide a service that operates task-based execution to map sets of API resources to one another. User will be able to specify mapping process and execution sequence.  Will support OpenAPI 2.* and 3.* specification files as entrypoints. Call sequence and mapping should all be able to be configured via web interface. Should be testable with mock data from web interface.

## Milestones

### OpenAPI milestones

- [ ] First digest of an OpenAPI specification file
- [ ] First redisplay of an OpenAPI specification file in console
- [ ] First redisplay of an OpenAPI specification file in web
- [ ] First navigation through models of a source system via web
- [ ] Able to execute a request from web
- [ ] Able to adjust various parts of a request (non-spec'd portions)
  - [ ] Parameters
  - [ ] Headers
  - [ ] Body

### Mapping milestones

- [ ] Able to execute a sequence of API calls
- [ ] Able to use fields from specification to modify params used in other calls (each call has reference to prior calls, and can manipulate params, etc)
- [ ] Able to choose sources from a resource and map to targets in another resource (can be same system or different systems)
- [ ] Able to preview and see examples of resources being mapped
- [ ] Simple mapping transformations (string -> number, date -> string, etc)
- [ ] Branching logic to control flow of sequences of API calls based on prior calls (if statements)
- [ ] Control logic to control flow of sequences of API calls based on prior calls (loops)
- [ ] Custom mapping transformations
  - [ ] Mapping base types
  - [ ] Mapping arrays
    - [ ] Array -> Array
    - [ ] Array -> Value
    - [ ] Value -> Array
  - [ ] Mapping complex types (objects)
    - [ ] Object -> Value
    - [ ] Object -> Array
    - [ ] Value -> Object
    - [ ] Array -> Object
    - [ ] Object -> Object
- [ ] Failure branches
  - [ ] Digestion of problem details and usage of props in branch logic
  - [ ] Termination of execution sequence
    - [ ] Simple, stop process and halt execution
    - [ ] Restorative, attempt to undo state-changing operations already completed
  - [ ] Retrying steps
  - [ ] Failure as a branch condition
    - [ ] All failure as a single condition
    - [ ] Multiple types of failure as separate conditions

### Authentication milestones

- [ ] Able to access specifications requiring auth to acquire
- [ ] Able to use various auths to access resources
  - [ ] Basic
  - [ ] Bearer
  - [ ] Digest
  - [ ] OAuth
- [ ] Auth QoL
  - [ ] Token acquisition
  - [ ] Token refresh
    - [ ] User-supplied timespan
    - [ ] Spec-provided timespan
    - [ ] Resource-provided timespan

### Testing

Undetermined as of yet. It may take experience as the system develops to determine a proper course of action here.

### Later goals

- [ ] Support XML (as opposed to just json)
- [ ] Break tasks apart from sequences, create list of tasks from API calls and use their dependencies to create the sequence
- [ ] Support for parallelization of tasks
- [ ] Outline resources for sites that do not have OpenAPI specifications
- [ ] Automated task execution (for a full sequence)
- More to come...

## Anticipated tech stack

- Web Frontend
  - Framework: [VueJS 3](https://vuejs.org/)
  - Base component library: [Quasar](https://quasar.dev/)
  - Language: [TypeScript](https://www.typescriptlang.org/)
  - Dependency management: [Yarn](https://www.typescriptlang.org/)
  - Builds: [Vite](https://vitejs.dev/)
  - SPA architecture
- Web Server
  - Framework: NET 6, AspNetCore
  - Database: Undetermined RDBMS
    - Probably just PostgreSQL initially
    - May add options for others if this picks up
  - Authorization: Undetermined
  - Deployment: Undetermined

## Challenges

- OpenAPI specification will continue to change in ways that could break the anticipated functionality of this tool
- Many sites may not have a specification actually meeting the OpenAPI spec
- Two different major versions of OpenAPI to support, may just support 3.* out of the gate and see if 2.* is still widely used afterwards