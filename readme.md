# Travis continuous delivery

[![Build Status](https://travis-ci.org/ldez/travis-continuous-delivery-hugo-deploy.svg?branch=source)](https://travis-ci.org/ldez/travis-continuous-delivery-hugo-deploy)

This project explains how to manipulate a Git repository within [Travis CI](https://travis-ci.org) to publish a static site build with [Hugo](https://gohugo.io/) on GitHub Page.

Use the [TravisCI primitive](https://docs.travis-ci.com/user/deployment/pages/) to deploy GH Pages.

## GitHub token

Get a [Personal Access Token](https://github.com/settings/tokens).

Only enable `public_repo` access for public repositories, `repo` for private.

You must defined environment variable via Travis:
- `GITHUB_TOKEN`: GitHub token

## Skip Build

### Commit message

Travis automatically skips the build if the commit contains `[ci skip]`.

- https://docs.travis-ci.com/user/customizing-the-build/#Skipping-a-build

Example:

```shell
git commit -m 'My commit message [ci skip]'
```

## Scaffolding

Install [Hugo](https://gohugo.io/)

```shell
git init travis-continuous-delivery-hugo-publish
cd travis-continuous-delivery-hugo-publish

git checkout -b source

cd ..
hugo new site travis-continuous-delivery-hugo-publish --force

cd travis-continuous-delivery-hugo-publish

hugo new post/first-post.md
echo 'Some text.' >> content/post/first-post.md
```
