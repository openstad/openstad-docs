# Git flow

This document describes the source management process used by the Openstad project. We use, as many other projects, a process called [Git Flow](https://github.com/nvie/gitflow), this document emphasizes interfacing with external developers/teams instead of reiterating [Git Flow documentation](http://bit.ly/OUNRqg) readily available on the Web.

## Overview

![git flow overview](../img/gitflow.svg)

Read Atlassian's awesome \[Git Flow documentation]\(https://www.atlassian.com/git/tutorials/comparing- workflows/gitflow-workflow) for more information.

## Branches & Repos

### master

* The latest stable release.
* Tagged according to 's versioning scheme.
* Commits merged from hotfix and release branches.
* Once released add date and version number to changelog

### development

* The work-in-progress next release.
* Commits merged from pull requests.

### feature/my-awesome-feature

* Development for a new feature
* These should be used in forks, not the official repositories
* Once the feature is completed the branch will be merged into development
* For every feature merged add to explanation to changelog

### release/x.y.z

* A release branch is opened as a code freeze some time before the next release based on the current develop-branch.
* Release branch should only include bugfixes to the features that will be in the next release.
* Any new features should be merged to develop-branch for a release after the next one.
* Once the release testing has been completed the branch will be merged into develop and master.

### hotfix/x.y.z

* When urgent bugfixes are required for the latest release a hotfix-branch is opened based on the current master-branch
* Once the fixes are completed the branch will be merged into develop and master
* For every hot fix merged add to explanation to changelog

###

#### External branches

The branching model utilized by an external team is generally irrelevant to the process of handling external contributions. It is, however, assumed for the purposes of this document that there exists a continuous sequence of commits from the latest merge from branches on GitHub to the commit(s) presented for consideration for inclusion in proper. This is required in order to be able to rebase such commits on the **develop** branch.

Code acquired from external sources will be subject to adaptation (if deemed necessary), normal _feature testing_ and bugfixes before it can be merged into the **development** branch.

## Creating releases

For creating a branch for version x.y.z

```
git checkout development
git pull
git checkout -b release/x.y.z
# TODO: Bump version at this point on the *release* branch (see below for instructions)

# Get the version commit to develop
git checkout development
git merge --no-ff release/x.y.z
# TODO: Bump next development version on the *development* branch (see below for instructions)
# Checkout to the release branch
git checkout release/x.y.z
```

Merging pull requests to release

```
git pull https://github.com/amsterdam/openstad-frontend.git some-bugfix
# git cherry-pick from develop etc
git push origin release/x.y.z
```

Merging changes back to master

```
git pull
git checkout master
git pull
git merge --no-ff release/x.y.z
git tag -a x.y.z -m "Release x.y.z"
git push origin master
git push origin --tags
```

Merging changes back to develop

```
git checkout development
git pull
git merge --no-ff release/x.y.z
# possible merging of conflicts
git push origin development
```

Cleanup

```
# remove local branch
git branch -D release/x.y.z
# remove remote branch
git push origin :release/x.y.z
```

## Versioning the code

* Releases should move the minor version 1.50.0 -> 1.51.0
*   Hotfixes should move the patch version so 1.50.0 -> 1.50.1

    ## Checkout to branch that should have the version updated

    git checkout {branch}

    ## Commit the changes to Git

    git add . git commit -m 'Bump version' git push

Develop branch version should always be the next version + "-SNAPSHOT". For an example if the version in master is "1.50.0", develop should be "1.51.0-SNAPSHOT".

## Creating hotfixes

Much like creating releases except hotfixes are based on the master version (releases are based on develop).

For creating a branch for version x.y.z

```
git checkout master
git pull
git checkout -b hotfix/x.y.z
```

Merging pull requests to hotfix

```
# TODO: Bump version at this point (see below for instructions)
git pull https://github.com/amsterdam/openstad-frontend.git hotfix/my-urgent-fix
# git cherry-pick from develop etc
git push origin hotfix/x.y.z
```

Merging changes back to master

```
git pull
git checkout master
git pull
git merge --no-ff hotfix/x.y.z
git tag -a x.y.z -m "Hotfix x.y.z"
git push origin master
git push origin --tags
```

Merging changes back to develop

```
git checkout development
git pull
git merge --no-ff hotfix/x.y.z
# possible merging of conflicts
git push origin develop
```

Cleanup

```
# remove local branch
git branch -D hotfix/x.y.z
# remove remote branch
git push origin :hotfix/x.y.z
```

## Credits

Most of this document has been taken from: https://oskari.org/documentation
