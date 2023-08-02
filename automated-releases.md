# Automated Releases

## What do automated releases do:

Automated releases generate a github release and build a release.tar or docker image for the given repository. It does this once a pull request has been merged into master or develop branches.

## Automated releases naming conventions

The goal is to follow Semantic Versioning as closely as reasonably possible. This should remove some cognitive load when deploying different projects. It also seems like a good idea to have an opinionated and widely used convention - considering the number of services we build and support.

When a release is created, the tag which corresponds to the release is named v followed by the version number found in the .release-version file, e.g. “v2.1.3”. The release name is simply the version number found in the .release-version file, e.g “2.1.3”.

## How the automated releases change will affect pull requests:

The only extra work required is on each pull request pointing into master you will need to bump the value in the .release-version file. For example if you have a minor change going into master you will be required to increment .release-version in your pull request from vX.0.3 to vX.1.0.

There is a github action check to make sure you are doing this called ‘check release version bump’. This check will fail if the value in the pull requests’ .release-version file has the same value as the latest release of the repo.<sup>1</sup>*

## Why do we need automated releases:

Automated releases are a stepping stone for the move over to automated deployment, in which the end goal is to be able to deploy an application on pull request merge.

## Hotfixes

Hotfixes into master are still possible except you will need to bump the value in the .release-version file.


## Branch deployments - before merging

For repos using Docker images as the unit of deployment, there is an “on dispatch” action which allows you to quickly build, tag and push a Docker image from a specific branch. This actions skips testing which allows for quicker deployment and testing. Try stick to semver when creating the tag: [https://semver.org/#spec-item-9](https://semver.org/#spec-item-9)

## Future plans/ideas

*   Move common actions to the organization’s templates in the “github” repo
*   On dispatch releases for asset creation
*   Improve version comparison check
*   Automated deployment - on merge into develop or master, it deploys to the related environment
*   Check if actions in a PR are re-run when other PRs are merged into the target

### Automated releases notes

1* Check release bump is quite crude and only compares the value in your .release-version file to the repo’s latest release tag name. Rely on this check lightly as there are some edge cases in which this will false pass. For example if you create a pull request and have bumped the .release-version file correctly and another pull request is merged in before yours, you will then need to bump your .release-version again to account for this. The test may still say it has passed if it hasn't been re-run. 
