# Scripts

This document describes the purpose of each script found in the `bin`
directory.

## ai-prompt

A Ruby script that generates a prompt for an AI model from an ERB
template. It reads a template file (e.g., `ai-prompt.erb`), processes it
to include project file contents, and copies the resulting prompt to the
macOS clipboard using `pbcopy`. It is designed to be run from the root
of a Git repository.

## bare-prompt

A simple shell script that sets the command line prompt (`PS1`) to a
minimalist `$ `.

## brew-bundle-dump

Updates the global Homebrew `Brewfile` by running `brew bundle dump`
with flags to include all installed packages (including Mac App Store
apps), add descriptions, and overwrite the existing file.

## create-profile-d

A shell script that creates the `/etc/profile.d` directory on macOS if
it does not already exist. This script requires root privileges to run.

## create-release-pr-labels

Uses the GitHub CLI (`gh`) to create a standard set of labels in a
repository for managing release pull requests. The labels include
`major-change`, `minor-change`, `patch-change`, `internal-change`, and
`release`.

## detect-shell-type

Inspects and reports the current shell\'s environment. It identifies the
shell executable, determines if the session is interactive and/or a
login shell, and shows version information for Zsh and Bash.

## dirs-in-my-path

Lists each directory in the `PATH` environment variable on a separate
line for easy viewing.

## docker-bash

Starts an interactive Bash session within a specified Docker image. It
can also execute a given command within the container instead of
starting an interactive shell.

## docker-nuke

Completely resets the local Docker environment by stopping all running
containers, then forcibly pruning all containers, images, networks, and
volumes.

## docker-prune

A less aggressive cleanup script for Docker. It stops any containers
specified as arguments, then prunes all unused containers, networks, and
images (with `-a`), and finally prunes all unused volumes.

## git-branch-prune

Deletes local Git branches whose upstream remote branch has been
removed. It first runs `git fetch --prune` to update remote-tracking
branches and provides options to force-delete branches or skip the
confirmation prompt.

## git-clone

Clones a Git repository into an organized directory structure based on
the repository\'s organization or user. For example, it clones
`git@github.com:jcouball/scripts.git` into `~/github/jcouball/scripts`.

## git-remotes

Reorganizes local Git repositories in the current directory. It finds
all subdirectories that are Git repositories, reads their remote
\'origin\' URL to determine the organization, and moves them into a new
directory named after that organization (e.g., `_jcouball`).

## git-status

Provides a detailed overview of the state of a Git repository by showing
the output of three distinct diff commands: changes between the working
directory and the index (`git diff-files`), the index and HEAD
(`git diff-index --cached HEAD`), and the working directory and HEAD
(`git diff-index HEAD`).

## git-wrapped

A wrapper script for the `git` executable, designed for development on
Git itself. It sets the necessary environment variables
(`GIT_EXEC_PATH`, `GIT_TEMPLATE_DIR`, etc.) to use a custom build of Git
instead of the system-installed version.

## launch-keeper

A macOS utility to back up and restore auto-launch configurations. It
saves a list of login items and copies user-level `LaunchAgents` plists,
allowing for easy restoration on a new or rebuilt system.

## non-git-subdirs

Scans the subdirectories of the current location and prints the names of
those that are not part of a Git repository. It is designed to be run
from a directory that is not itself within a Git work-tree.

## remove-icon-files

A Ruby script that recursively finds and deletes custom macOS icon files
(`Icon\r`) from a specified directory. It includes options for a dry run
(to list files without deleting) and logging.

## reset-test

A simple utility script that removes and then recreates the directory
`~/my_test`, providing a clean slate for testing purposes.

## reuse-ssh-agent

Finds and connects to a running `ssh-agent` process to reuse it for the
current shell session. If no active agent is found, it starts a new one.
This script is intended to be sourced in a shell startup file like
`.zshrc` or `.bashrc`.

## rubocop

A wrapper script that executes the `rubocop` command using the version
specified in the current project\'s `Gemfile`, ensuring consistent style
checks.

## ruby-wrapper

A sophisticated wrapper for running a Ruby script from a specific gem in
an isolated environment. It uses `asdf` to manage the Ruby version and
`bundler` to manage the gem and its dependencies within a dedicated
directory (`~/.local/share/<gem-name>`), which it automatically cleans
monthly.

## ruby-wrapper-list

Lists all the isolated Ruby gem environments that have been created by
the `ruby-wrapper` script in the `~/.local/share` directory.

## run-until-fail

Executes a given command repeatedly in a loop until it fails (i.e.,
returns a non-zero exit code). It reports the number of successful runs
before the failure.

## shell-mode-functions

A collection of POSIX-compatible shell functions
(`is_interactive_shell`, `is_login_shell`, etc.) to reliably determine
the operating mode of the current shell. This script is meant to be
sourced, not executed directly.

## src-clean

A powerful Ruby script for cleaning a source directory by comparing it
against a target directory. It moves files that are unique to the source
into the target, and deletes files from the source that are identical to
their counterparts in the target. Finally, it removes any empty
subdirectories left behind in the source.

## sshagent

A script containing functions to manage SSH agent connections, with
special handling for `yubico-agent` on macOS and standard `ssh-agent` on
Linux. It is intended to be sourced into a shell environment.

## upgrade-all

A comprehensive update script for macOS. It automates the process of
updating Homebrew, upgrading all installed formulae and casks, cleaning
up old versions, and upgrading all Mac App Store applications via `mas`.

## xcode-version

A macOS script that reports the installed versions of Xcode and the
command-line developer tools by querying the `pkgutil` database.
