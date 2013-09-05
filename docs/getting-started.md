---
toc-index: 1
layout: default
title: Getting Started
---   

*Eventually, Node-RED will be installable using npm. Until then, the following
guide will help you get started.*

### Install node.js

You can get the latest version from <http://nodejs.org/download/>.

Or, you may want to use a version from your operating system's package manager:
 <https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager>

### Install the pre-requisite modules

From the top-level directory of Node-RED, run:

    $ npm install

This will install the core pre-requisite modules.

### Run Node-RED

From the top-level directory, run:

    $ node red.js

You can then access Node-RED at <http://localhost:1880>.

By default, Node-RED uses a file called `flows_<hostname>.json` to save the
deployed configuration. You can point to a different flow file at start-up:

    $ node red.js my_flows.json


### Installing individual node dependencies

*Eventually, nodes will be npm-installable themselves. This will take care of
all of the dependency management. Until then, it is a bit more manual...*

When Node-RED starts, it attempts to load the nodes from the `nodes/` directory.
Each will have its own set of dependencies that will need to be installed before
the node is available in the palette.

To help identify the dependencies, Node-RED logs any modules it fails to find
for a particular node. You don't have to install these unless you want or need
that node to appear.

Alternatively, a node's `.js` file can be examined to identify the modules it
explicitly requires. For example, the Twitter node is defined in
`nodes/social/27-twitter.js` and contains:

	var RED = require("../../red/red");
	var ntwitter = require('ntwitter');
	var OAuth= require('oauth').OAuth;

Of these, `ntwitter` and `oauth` are neither built-in modules nor ones provided
by Node-RED itself. They can subsequently be installed by running:

    $ npm install ntwitter oauth
