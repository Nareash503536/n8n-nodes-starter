# n8n-nodes-starter

This repo contains example nodes to help you get started building your own custom integrations for [n8n](n8n.io). It includes the node linter and other dependencies.

## Prerequisites

You need the following installed on your development machine:

* [git](https://git-scm.com/downloads)
* Node.js. Minimum version Node 18. You can find instructions on how to install both using nvm (Node Version Manager) for Linux, Mac, and WSL [here](https://github.com/nvm-sh/nvm). For Windows users, refer to Microsoft's guide to [Install NodeJS on Windows](https://docs.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-windows).
* Recommended: follow n8n's guide to [set up your development environment](https://docs.n8n.io/integrations/creating-nodes/build/node-development-environment/).

## Using this starter

These are the basic steps for working with the starter. For detailed guidance on creating and publishing nodes, refer to the [documentation](https://docs.n8n.io/integrations/creating-nodes/).

Refer https://github.com/n8n-io/n8n-nodes-starter start with a new custom node

### Create a custom node

1. Run 'npm install'
```
	hint: The console may give a warning/error on missing pnpm. Ignore that.
```
2. Go to `repo-path/nodes/<custom-node-name>`
2. Add relevant files to the directory
3. Add the path of the new custom node to `repo-path/package.json` under
```
"n8n": {
    "n8nNodesApiVersion": 1,
    "credentials": [
      ...
    ],
    "nodes": [
      "dist/nodes/<custom-node-name>/<custom-node-name>.node.js"
    ]
  }
```
4. Now run `npm run build`
	- Directory `repo-path/dist` will get generated.
5. Now copy `repo-path/dist/nodes` and paste it in `~/.n8n/custom`
6. Now restart the n8n instance and the modifications will be updated(New custom node can be seen).

### Create a custom credential

1. Run 'npm install'
```
	hint: The console may give a warning/error on missing pnpm. Ignore that.
```
2. Go to `repo-path/credentials/<custom-credential-name>`
2. Add relevant files to the directory
3. Add the path of the new custom node to `repo-path/package.json` under
```
"n8n": {
    "n8nNodesApiVersion": 1,
    "credentials": [
	"dist/credentials/<custom-credential-name>.credentials.js",
    ],
    "nodes": [
    	...
    ]
  }
```
4. Now run `npm run build`
	- Directory `repo-path/dist` will get generated.
5. Now copy `repo-path/dist/credentials` and paste it in `~/.n8n/custom`
6. Now restart the n8n instance and the modifications will be updated(New custom node can be seen).


### Live modifications when development

1. Run 'npm install'
```
	hint: The console may give a warning/error on missing pnpm. Ignore that.
```
2. Go to `repo-path/nodes/<custom-node-name>`
2. Add relevant files to the directory
3. Add the path of the new custom node to `repo-path/package.json` under
```
"n8n": {
    "n8nNodesApiVersion": 1,
    "credentials": [
      ...
    ],
    "nodes": [
      "dist/nodes/<custom-node-name>/<custom-node-name>.node.js"
    ]
  }
```
4. Now run `npm run build`
	- Directory `repo-path/dist` will get generated.
5. Now run `npm link`
```
hint: The console may give a warning/error on missing pnpm. Ignore that.
```
- Run `npm -g list` to see the global packages
```
-- n8n-custom-nodes@...
`-- n8n@1.40.0
...
```
6. Now run `npm link <custom-node-package-name>` inside the `~/.n8n/custom` path.
- The `custom-node-package-name` here is `n8n-custom-nodes`
7. Now restart the n8n instance and the modifications will be updated(New custom node can be seen).

### Troubleshooting

- There's no custom directory in ~/.n8n local installation.
	
You have to create custom directory manually and run npm init
```
# In ~/.n8n directory run
mkdir custom 
cd custom 
npm init
```

## More information

Refer to our [documentation on creating nodes](https://docs.n8n.io/integrations/creating-nodes/) for detailed information on building your own nodes.
