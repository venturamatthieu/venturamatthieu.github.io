# Init service like a devops

## GitLab 

- Create repository 
- Defined access
- Prepare bot to get event (collab team tools) 
- Define pipeline steps 

## Branch strategy
You have to use Git Flow strategy.

![](https://uploads.toptal.io/blog/image/129305/toptal-blog-image-1551794424851-b3d5928bc33edfc954ef460062e5cbcc.png)

## Commit Convention, Semantic Release and Tag

We have to display a readable changelog.

You have to apply convention in your future commit to automize.

[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

Specifying the Type of Change type must be one of the following: 
- feat: A new feature 
- fix: A bug fix 
- docs: Documentation-only changes 
- style: Changes that do not affect the meaning of the code, such as changes to whitespace, formatting, missing semicolons, and so on 
- refactor: A code change that neither fixes a bug nor adds a feature 
- perf: A code change that improves performance 
- test: Changes that add missing tests
- chore: Changes to the build process or auxiliary tools and libraries, such as documentation generation

Specifying the Scope of a Change:
- Environment: Examples include prod, uat, and dev 
- Technology: Examples include RabbitMq, SOAP, JSON, Puppet, build, and JMS 
- Feature: Examples include pricing, authentication, monitoring, customer, shoppingcart, shipping, and reporting
- Product: Examples include books, dvd, vod, jewel, and toy 
- Integration: Examples include Twitter and Facebook 
- Action: Examples include create, amend, revoke, and dispute

Example of commit : feat(pricing, vod): increase the rate on prime time

Tools : 
- https://github.com/commitizen/cz-cli
- https://github.com/conventional-changelog/conventional-changelog

Links :
- https://keepachangelog.com
- https://semver.org/
- https://www.conventionalcommits.org/

## Hooks

List of most usefull hook :  
```shell
pre-commit
prepare-commit-msg
commit-msg
post-commit
post-checkout
pre-rebase
```
Use plugin to configure project hook :
https://github.com/typicode/husky

## Evergreen Readme


### Information and quality

What is it ? How does it work? Who use it ? What is it goal ? How can the organization benefit from using ?


| Stable Release | Coverage % | Open Issues |
|:----------------|:----------|:----------|
| 1.1.2 | 55 | 1 2|

| Branch | CI Step 1 | CI Step 2 | CI Step 3 | CI Step 4 | CI Step 5 |
| :------|:----------|:----------|:----------|:----------|:----------|
| master | pass | pass | fail | fail | fail |
| dev    | pass | fail | fail | fail | fail |

### How to build ? to run ? test ? doc ?

```shell
cd ./myService
build.sh
run.sh
test.sh
doc.sh
```




## CI Pipeline 

Default template ???

## Deploy locally

Kub or Traefik ???
