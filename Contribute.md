# Contributing Guidelines
This document outlines the process to help get your contribution accepted.

## Sign Your Work with your GPG key
    git commit -s -m ...
 
The sign-off is a simple line at the end of the explanation for a commit. All commits needs to be signed. Your signature certifies that you wrote the patch or otherwise have the right to contribute the material.

For help generating your GPG check the following:

 [GitHub](https://help.github.com/en/github/authenticating-to-github/managing-commit-signature-verification)
 
[Bitbucket](https://confluence.atlassian.com/bitbucketserver/using-gpg-keys-913477014.html)
## Conventional Commits
    The commit message should be structured as follows:

    <type>[optional scope]: <description>

    [optional body]

    [optional footer(s)]
where "scope" should be Jira ticket number

## Example
    git commit -s -m "feat[HELM-101]: Added readme file"
for the full specification check [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
