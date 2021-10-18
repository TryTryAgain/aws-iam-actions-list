# aws-iam-actions-list

A list of all known Amazon Web Services' IAM actions; and a way of updating that list.

# Why?

Because sometimes it's just handy to have the list of IAM actions, all in one
place.  For example, if you can _almost_ remember the name of the action, but
not quite, this list can be quite a handy reference.

It's also informative to observe the history of the list, as new actions are
added.

I wish AWS provided this information themselves somewhere, in a supported,
machine-readable form.  But if they do provide it, I haven't found it yet. 

Follow https://gitlab.com/TryTryAgain/aws-iam-actions-list/-/issues/1 for
similar content and related resources.

# Using the list

It's one action per line, plain text format: `all-actions.txt`

For example, to see all CloudWatch Events actions: `grep ^events: all-actions.txt`

# Browsing/Searching commit history

Along with having the all-actions.txt file, the project also makes it easy to
follow along, commit messages will dynamically list what is completely New/Removed
as well as what had actions added to or taken away from, using the language below:

- New Services: 'xyz'.
- Added actions to 'abc,xyz'.
- Removed Services: 'lmno'.
- Removed actions from 'abc'.

Meaning on GitLab for example you can search using regex for `Added.*rds` to surface
all the times RDS has received updates/additional actions added...or `Removed.*rds`
to see what's ever been removed.

# Updating the list

Depends on bash, curl, ~~ruby~~, node, and jq.

## Manually

Run `make update`; review the results.

## GitLab CI/CD

See [.gitlab-ci.yml](.gitlab-ci.yml)

The update works by reading JavaScript assets used by the AWS Policy Generator
<https://awspolicygen.s3.amazonaws.com/policygen.html>.  It's very much an
unsupported method though, so the update scripts might need updating from time
to time.

# License
Licensed under the Apache License, Version 2.0.  See the LICENSE file.

- Original project (aws-iam-reference): https://github.com/rvedotrc/aws-iam-reference
- Removed ruby dependancy: https://github.com/rvedotrc/aws-iam-reference/pull/1
- Found new policies URL: https://github.com/rvedotrc/aws-iam-reference/pull/4
- Made commits more informative and maintain moving forward (aws-iam-actions-list): Michael Lawler @TryTryAgain
  - Add descriptive commits to update-and-commit and retroactively `git filter-branch`; forcibly replacing all generic "Automatic commit of updated actions" occurrences with dynamic Added/Removed messages, matching the style introduced by the commit that introduced descriptive commits.
  - Hosted on GitLab.com https://gitlab.com/TryTryAgain/aws-iam-actions-list
  - Mirrored from GitLab.com to GitHub.com https://github.com/TryTryAgain/aws-iam-actions-list
