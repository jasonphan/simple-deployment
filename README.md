# simple-deployment

Tool for deploying frontend projects using Vue/React and backend servers using Node.js/Express. This tool is built on Bash and uses SSH in the background.

## Requirements

[Git](https://git-scm.com/) and [Node.js](https://nodejs.org/en/) required on the remote server.

[PM2](https://pm2.keymetrics.io/) required when deploying a Node backend.

Add your SSH key to your deployment user.

## Getting Started

Modify the configuration variables within the `dep` file.
```
# User with access to the remote server.
remote_user=""

# Host of the remote server.
remote_host=""

# Root folder of the project to be deployed.
project_root=""

# Default git branch of the project.
git_default_branch="develop"
```

Copy the `deploy` file to your project root on the remote server.

Modify the configuration within the `deploy` file.
```
# Files that are shared between releases.
shared_files=(
    'client/.env'
    'server/.env'
)

# Site URL of the project to be deployed.
site_url=""

# Number of releases to be kept from deployment.
max_releases=5

# The project node build command.
build="run build"

# Relative client folder path from project root.
client_path="client"

# Relative server folder path from project root.
server_path="server"

# Node server entrypoint file.
server_file="index.js"

# PM2 name alias for the server.
server_alias="server_alias"

# The git repository of the project.
repository=""
```

Add executable permissions on both `dep` and `deploy` files.
```
# On local
chmod +x dep

# On remote
chmod +x deploy
```

To deploy, run `./dep your-branch` or `./dep` locally.

Omitting the branch argument will deploy your default branch.
