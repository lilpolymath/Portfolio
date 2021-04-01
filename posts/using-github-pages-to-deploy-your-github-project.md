---
templateKey: blog-post
title: Using GitHub Pages to deploy your GitHub Project
date: 2020-07-18T20:11:24.568Z
tags: react, github, static
thumbnail: /image/github-pages.jpeg
slug: using-github-pages-to-deploy-your-github-project
description: A quick example that shows how to deploy a project on GitHub using GitHub pages.
---

GitHub Pages is a static site hosting service that takes HTML, CSS, and JavaScript files straight from a repository on GitHub, optionally runs the files through a build process, and publishes a website.

It was created by GitHub to allow developers to host their projects directly from a GitHub repository without having to pay for domain cost.

You can publish a website about to `https://<username>.github.io` and your project to `https://<username>.github.io/{your-project-name}`.

The purpose of this article is to guide you through publish your project with gh-pages whether it is a plain HTML, CSS & JavaScript project or it is built with React xD.

### Plain HTML, CSS & JS

1. If your website contains images make sure that they are not stored in a media folder as gh-pages doesn't parse relative imports well. You may have to upload your images to a service like Cloudinary.

2. With that out of the way, navigate to your repository settings and locating the GitHub Pages section
   ![image](https://i.imgur.com/5ZlMuH7.png)

3. Select the master branch from the drop down menu and this triggers a refresh.
   ![image](https://i.imgur.com/PDUMDMZ.png)

4. When the page is done refreshing, navigate back to the GitHub Pages section and it should be active with the URL to the live project active.
   ![image](https://i.imgur.com/T7EH5CC.png)

Note that because of this setting each commit you make to the master branch updates the live project too.

### React Project.

1. Install gh-pages by running

`npm install gh-pages` or `yarn add gh-pages`

This packages creates a `gh-pages` branch that would hold the build files for your project.

2. In your package.json file
   add the following line

```
"homepage": "https://<username>.github.io/<repo-name>",
```

Note that the repo name can be anything not necessarily generic.

3. Also update your scripts to contain

```
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    ....
   },
```

The predeploy command generates a build that is ready to be published while the deploy command generates a build then deploys it

4. When you are ready run

```
npm run deploy
```

Wait for it to finish deploying the site and check the URL you set as homepage in your package.json to view it.

If you get the error
`git remote add origin https://github.com/lilpolymath/test-repo.git git push -u origin master`
run

```
rm -rf node_modules/gh-pages/.cache
```

that clears the cache for you and rerun the deploy command.
