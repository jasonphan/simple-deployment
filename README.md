# Simple Deployment Tool
For deploying sites from frontend frameworks such as Vue.js

## Getting Started
Clone this repository.

Modify the configuration within the `dep` file.
```
# User to log into the remote server.
user=""

# Host of the remote server.
hostname=""

# Root folder of the project to be deployed.
project_root=""

# Default branch of the project.
default_branch=""
```

Move the `deploy` file to the root folder of your project on the remote server.

Modify the configuration within the `deploy` file.
```
# Files that are shared between releases.
shared_files=(
    '.env'
)

# Site URL of the project to be deployed.
site=""

# Number of max releases to be kept by the deployment tool.
max_releases=5

# The project node build command.
build="run build"

# The git repository of the project.
repository=""
```

Add executable permissions on both `dep` and `deploy` files.
```
chmod +x dep
chmod +x deploy
```

Make sure your ssh key is added to the remote server.

To deploy run `./dep your-branch` or `./dep` to deploy your default branch.
