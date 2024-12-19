---
title: About This Site
---

# About This Site

## Contributing

### Trivial Changes

_(for those with commit access)_

At the bottom of each page is an `edit this page` button. Clicking this will open up GitHub's web text editor where you can make text changes and commit. Alternatively you can use GitHub's VS Code interface from the repo page by clicking the `.` key.

### Significant Changes

_(for anyone)_

- Please fork the repo (for non-members of the repo, the `edit this page` option at the bottom of each page will walk you through this)
- Web-based
  - Once the repo is forked, go to the repo page and click `.`: this will open VS Code in the browser
  - Checkout a branch (bottom left, second option in)
  - Make your edits
  - In the left vertical menu, select the source control option
  - Enter a message about your changes and click `commit and push`
- Local-based (terminal commands for example, use GUI client if you wish)
  - Clone the repo `git clone https://github.com/YOURUSERNAME/dev.luanti.org`
  - Make a branch `git checkout YOUR_BRANCH_NAME`
  - Make edits with the tools of your choosing
  - Add, commit, and push the changes: `git add -A && git commit -m "YOUR COMMIT MESSAGE HERE" && git push`
- Make a PR from the branch back to the repo
- Wait for someone on the Luanti docs team to review and merge

### Building and Running Locally

_(anyone)_

To build locally, you will need to first [install Hugo](https://gohugo.io/installation/).

When cloning the repository you need to clone it recursively so that the theme submodule gets included:

```bash
git clone --recursive https://github.com/minetest/dev.luanti.org
```

If you have already cloned you can fetch the submodules as such:

```bash
git submodule init
git submodule update --remote
```

To launch the Hugo development server run `hugo server`. It will watch and regenerate whenever changes are made.

To generate the site once without starting the server you can simply run `hugo`.

## Contribution Rules

**This is subject to change**

- For non-trivial changes, please make a PR (branches are disabled on the main repo)
- Squash and merge PRs only (other methods are disabled on the repo)
- We nicely ask that you announce changes (in optional minutes) in the #minetest-docs IRC/Discord/Matrix channel
