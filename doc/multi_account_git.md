# Multi-account Git Configuration

## Check my current user-level Git configuration

``` shell
git config --global --list
```

## New setup

``` shell
# --- Optionally use a separate testing Git configuration file

# This avoids modifying the default global Git configuration.
export GIT_CONFIG_GLOBAL=~/.gitconfig-test1

# Now Git should fail reading the configuration file
git config --global --list
# fatal: unable to read config file '/home/vbrozik/.gitconfig-test1': No such file or directory

# --- Create new Git configuration - example with my data

# Set the user information which will be used in commits
git config --global user.name 'Václav Brožík'
git config --global user.email '5073939+vbrozik@users.noreply.github.com'
# Set the newly recommended default branch name for new repositories.
# The name main is the default in GitHub repositories for years already and it will become the standard in Git as well.
git config --global init.defaultBranch main
# Use Git Credential Manager from Windows for authentication
# git config --global credential.helper manager
git_win_exec_path="$(wslpath -u "$(git.exe --exec-path)")"
gcm_win_path="$(dirname "$(dirname "$git_win_exec_path")")/bin/git-credential-manager.exe"
# /mnt/c/Program Files/Git/ucrt64/bin/git-credential-manager.exe
git config --global credential.helper \!"'$gcm_win_path'"

# Verify the new configuration
git config --global --list
```

## How to use the new Git configuration

``` shell
git clone https://vaclav-brozik_nttltd@github.com/NTT-EU-CZ/cz-git-training-sandbox.git
```
