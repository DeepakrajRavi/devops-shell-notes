# 🔐 GitHub API Script – List Collaborators with Read Access

This Bash script uses the GitHub REST API to list all users who have **read access** to a specified repository.

## 📋 Features
- Uses GitHub API with Basic Auth
- Lists users with `pull` permission
- Helpful for auditing collaborators

## 💻 How to Use

1. Replace `$username` and `$token` with your GitHub username and [Personal Access Token](https://github.com/settings/tokens).
2. Run the script with the repo owner and name as arguments:

```bash
./list-read-users.sh <owner> <repo>
Example:
./list-read-users.sh DeepakrajRavi devops-shell-notes
📜 Script Code
#!/bin/bash

# GitHub API URL
API_URL="https://api.github.com"

# GitHub username and personal access token
USERNAME=$username
TOKEN=$token

# User and Repository information
REPO_OWNER=$1
REPO_NAME=$2

# Function to make a GET request to the GitHub API
function github_api_get {
    local endpoint="$1"
    local url="${API_URL}/${endpoint}"
    curl -s -u "${USERNAME}:${TOKEN}" "$url"
}

# Function to list users with read access to the repository
function list_users_with_read_access {
    local endpoint="repos/${REPO_OWNER}/${REPO_NAME}/collaborators"
    collaborators="$(github_api_get "$endpoint" | jq -r '.[] | select(.permissions.pull == true) | .login')"

    if [[ -z "$collaborators" ]]; then
        echo "No users with read access found for ${REPO_OWNER}/${REPO_NAME}."
    else
        echo "Users with read access to ${REPO_OWNER}/${REPO_NAME}:"
        echo "$collaborators"
    fi
}

# Main script
echo "Listing users with read access to ${REPO_OWNER}/${REPO_NAME}..."
list_users_with_read_access
