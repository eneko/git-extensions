# git-extensions
Custom commands for `git` that I use.

## Installation
Git commands are scripts run by `git`. They must reside in a folder in your path and must be executable by your user. Instead of placing them in `/usr/local/bin` or similar, I recomend placing them inside a `bin` folder in your home directory.

On your home directory, create a `bin` folder (if you don't have one already):

`$ mkdir -p ~/bin`

Add that folder to your PATH for the scripts to be accessible by `git`:

`$ vim ~/.bash_profile`

Append the line:

`export PATH="$HOME/bin:$PATH"`

Save the scripts from this repository to `~/bin` and make them executable with `chmod`:

`$ chmod 755 <filename>`

## Usage

### git purge
`git purge` removes any tracked local branches that no longer exist in remote, and pulls the latest code changes. It relies on the status of `git branch -vv` to detect 'gone' branches. Because this command also pulls the latest code, I use it instead of `git pull` when working on projects with where bug and/or feature branches are used on a daily basis.

```
$ git purge
Pulling latest code...
Already up-to-date.
Deleting local branches that were removed in remote...
From https://github.com/yourteam/yourrepo
 - [deleted]         (none)     -> origin/feature/your-feature-branch
Done.
```

### git purgetags
`git purgetags` removes any local tags not found on remote. It relies on the fact that all tags can be removed locally and then fetched again from remote. I rarely use this command, mainly to sync my local when new releases are made.

```
$ git purgetags
Deleting local tags and pulling from remote...
Deleted tag '0.0.1' (was 4f40861)
Deleted tag '0.0.2' (was 3af9fa1)
Deleted tag '0.0.3' (was a6988d1)
From https://github.com/yourteam/yourrepo
 * [new tag]         0.0.1      -> 0.0.1
 * [new tag]         0.0.2      -> 0.0.2
 * [new tag]         0.0.3      -> 0.0.3
Done.
```
