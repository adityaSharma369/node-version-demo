## gh-action-bump-version

GitHub Action for automated npm version bump.

This Action bumps the version in package.json and push it back to the repo. 
It is meant to be used on every successful merge to master but 
you'll need to configured that workflow yourself. You can look to the
[`.github/workflows/push.yml`](./.github/workflows/push.yml) file in this project as an example.

### Workflow

* Based on the commit messages, increment the version from the lastest release.
  * If the string "BREAKING CHANGE" or "major" is found anywhere in any of the commit messages or descriptions the major 
    version will be incremented.
  * If a commit message begins with the string "feat" or includes "minor" then the minor version will be increased. This works
    for most common commit metadata for feature additions: `"feat: new API"` and `"feature: new API"`.
  * All other changes will increment the patch version.
* Push the bumped npm version in package.json back into the repo.
* Push a tag for the new version back into the repo.
