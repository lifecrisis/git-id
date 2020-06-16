# git-id

A command-line manager for your Git identities.

## Introduction

As a consulting programmer and free software contributor, I maintain
a number of "identities" that I use to commit to shared Git repositories
around the web.  Such "identities" include attributes that are normally
managed manually in one's `~/.gitconfig` file (e.g., `user.email`).

If a developer wants to use one machine to develop under multiple
identities, Git offers the `user.useConfigOnly` option.  This option tells
`git` to look for identity information in the `.git/config` file in each
repository.  This is a helpful, but incomplete, solution.

Suppose I have cloned a number of repositories to my machine associated with
a particular organization.  Since I have multiple identities, each of these
repositories will have its own identity configuration, so all of them must
be updated manually if my Git author credentials for that organization
change.

The `git id` tool provided by this repository solves this problem by
allowing the user to store and reuse their identities across multiple
repositories.  Updates to an identity are immediately reflected in all of
the repositories on your workstation that use that identity.  This saves
time for a busy developer.

## Installation

Installing this tool is simple.  The only prerequisites are that you have
a `~/bin` directory and that it is in your `$PATH`.  The tool is implemented
in `bash` for now, so you will need a Bash interpreter on your machine.

Clone this repository, `cd` into the repository and run:

```
$ git config --global user.useConfigOnly true
$ make install
```

The script will be placed in your `~/bin` directory and will be available
for use immediately.

## Usage

At this point, `git id -h` can be run to view the available options.  Read
this output carefully.  The interface is purposefully minimal and easy to
learn.

In summary:
  - Use `git id` to print your current commit author attributes.
  - Use `git config ...` to update the attributes in the current repository.
  - Use `git id -s name` to save the attributes.
  - Use `git id -u name` in another repository to use an existing identity.

**Note:** Subsequent changes to an identity in one repository will be
reflected in all other repositories that have "used" that identity.  This is
the most important feature of this tool.

## Development Status

The `git id` utility is very much a *minimum viable product*.

A number of improvements could be made that the author is already aware of.
For example, option processing could be made more robust.  Attributes could
be checked for their type.  Tab-completion could be added.  And so on...

Ultimately, this is just a proof of concept of a user interface.  I wrote it
to see if it would become at all popular.  If development of this tool is
ever taken seriously, it should probably be re-written in C and included
with Git.

It works for me, and that is good enough for now.
