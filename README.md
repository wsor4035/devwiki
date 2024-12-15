# Luanti Developer Wiki
Hosted by GitHub Pages, generated with [Hugo](https://gohugo.io/).

Theme: [hugo-book](https://themes.gohugo.io/themes/hugo-book/)

See [/content](/content/) for content.

## Building locally
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
