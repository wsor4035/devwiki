---
title: About This Site
---

# About This Site

## Contributing

### Trival Changes
*(for those with commit access)*

At the bottom of each page is an `edit this page` button. Clicking this will open up githubs web text editor where you can make text changes and commit. Alternatively you can use githubs vscode interface from the repo page by clicking the `.` key.

### Significant Changes
*(for anyone)*

* Please fork the repo (for non members of the repo, the `edit this page` option at the bottom of each page will walk you through this)
* Web based
    * Once the repo is forked, go to the repo page and click `.` - this will open vscode in the browser
    * Checkout a branch (bottom left, second option in)
    * Make your edits
    * In the left veritical menu, select the source control option
    * Enter a message about your changes and click `commit and push`
* Local based (terminal commands for example, use gui client if you wish)
    * Clone the repo `git clone https://github.com/YOURUSERNAME/dev.luanti.org`
    * Make a branch `git checkout YOUR_BRANCH_NAME`
    * Make edits with the tools of your choosing
    * Add, commit, and push the changes `git add -A && git commit -m "YOUR COMMIT MESSAGE HERE" && git push`
* Make a pr from the branch back to the repo
* Wait for someone on the minetest docs team to review and merge

### Building+Running Locally
*(anyone)*

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

* for non trival changes, please make a pr (branches are disabled on the main repo)
* squash and merge prs (other methods are disabled on the repo)
* nicely ask that you announce changes (in optional minutes) in the #mintest-docs irc/discord/matrix channels

