# Challenge 04

## CI/CD pipelines

CI/CD: Continuous integration, continuous deployment

#### Continuous integration

- The goal is to find and resolve problems early.

- We make changes locally, then commit them to the remote repo (and likely this all takes place on a separate branch that will be merged to main).


#### Continuous delivery and deployment

- The integrated code is compiled into artifacts and stored.

- The artifacts can be used in additional testing (linting & unit testing) before being ready for deployment.

- Artifacts are deployed to live environments for production use.

## The workflow

#### Push

A push takes place, either to the master or another branch (whichever one we're checking).

#### Lint Check & Unit Testing

Linting enforces coding standards and catches easily detectable bugs like typos and race conditions.
Unit tests check code at the component level - testing individual functions exposes problems closer to the source.

#### Build

Build an image of the project using something like Docker, which then gets uploaded to a package registry (something like Google Cloud Platform, which can store and run the image).
The purpose is to compile the code (and any dependencies) into binary, i.e. a machine-readable format.
Artifacts are meant to live beyond the build process - they are stored in registries to keep them accessible.
This accomplishes the "delivery" portion of CI/CD; By delivering a build to a package registry, we make it ready to deploy at any time.

#### Test

Automated testing continuously checks for errors

#### Deploy

Deploy the project to a staging or production environment.

## The Challenge

Create a new repo, containing a "Hello World" Python script.

Then, create a workflow that does the following:

- Job 1: Test
    - Check out the repo
    - Run the script
- Job 2: Build
    - Depends on Job 1
    - Check out the repo
    - Create an artifact
