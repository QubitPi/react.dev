---
title: Node.js Setup
---

<Intro>

First, install node.js with [Nodesource](https://deb.nodesource.com/), the Universal node & npm installer.

[Node Version Manager](https://github.com/nvm-sh/nvm) is a tool that helps us manage Node versions and is a convenient
way to install Node. Think of it as npm or Yarn that helps manage Node packages, but instead of packages, NVM manages
Node versions.

This also means we can install multiple Node versions onto your machine at the same time and switch among them if
needed.

</Intro>

<YouWillLearn>

* Switching Node.js Versions with NVM

</YouWillLearn>

## Displaying a List of Node.js Versions {/*displaying-a-list-of-nodejs-versions*/}

We can now view all the versions we downloaded so far with

```bash
nvm ls
```

The list then appears:

![Error loading node-versions.png](../images/node-versions.png)

The first three lines show the list of Node versions with the arrow pointing to the 14.18.1 version that is currently in
use; when a version is used, it displays as green.

## Switching Among Node.js Versions {/*switching-among-nodejs-versions*/}

The best feature about NVM is the ability to easily switch between different Node versions. Say we must use version
16.13.0 and then switch to 12.22.7; we can simply run either `nvm use 12.22.7` or `nvm use 16.13.0` to easily switch
into either version we need.

## Troubleshooting {/*troubleshooting*/}

### Changing Node Version {/*changing-node-version*/}

<Pitfall>

This answer does not support Windows OS

</Pitfall>

Suppose we would like to down-grade version from 18 to 14, then we can use `n` for node's version management like this.
[There](https://www.npmjs.com/package/n) is a simple intro for `n`.

```bash
npm install -g n
n 6.10.3
```

This is very easy to use. then we can show our node version:

```bash
node -v
v6.10.3
```

The available node versions can be found on Node's [release page](https://nodejs.org/en/about/previous-releases)

For windows [nvm](https://github.com/coreybutler/nvm-windows) is a well-received tool.

### "npm install" Error {/*npm-install-error*/}

#### GitHub Operation Times Out {/*github-operation-times-out*/}

```bash
git config --global url."https://".insteadOf git://
```

This will change all of our urls so that they all start with `https://` which shall be working for us.

#### node-sass Version Issue {/*node-sass-version-issue*/}

Running `npm install` gives

```bash
.node-gyp/18.7.0/include/node/v8-internal.h:646:38: error: no template named 'remove_cv_t' in namespace 'std'; did you
mean 'remove_cv'?
```

What we're seeing is an error during compilation of node-sass. That's a package processing our Sass/SCSS styles, which
is written in C++ and only re-packaged as a JavaScript library. The fact it's written in C++ means it needs to be
compiled on our device during installation (this is internally done by a tool called node-gyp, which we can spot in
the error output, too).

__The problem is node-sass with the specified version in package.json doesn't support Node version installed on the
machine__. The [node-sass community](https://github.com/sass/node-sass) needs time to catch up to support it (and
that's fair, as it's a volunteer-driven project).

Case-by-case solutions would be either upgrading sass versions or [downgrading Node](#change-node-version)
