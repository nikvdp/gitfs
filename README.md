gitfs [![Build Status](https://drone.presslabs.net/api/badges/PressLabs/gitfs/status.svg?arrra)](https://drone.presslabs.net/github.com/PressLabs/gitfs) [![Coverage Status](https://coveralls.io/repos/PressLabs/gitfs/badge.png?branch=HEAD)](https://coveralls.io/r/PressLabs/gitfs?branch=HEAD)
========

# Welcome to GitFS


gitfs is a [FUSE](http://fuse.sourceforge.net/) file system that fully
integrates with git. You can mount a remote repository's branch locally, and any
subsequent changes made to the files will be automatically committed to the
remote.

## Installation

GitFS is `pip` installable, but requires some extra settings. First create a
directory where GitFS can store it's working files and make sure your user has
permissions to modify it:

```bash
mkdir -p /var/lib/gitfs
chown -R $USER:$USER /var/lib/gitfs
```

Verify that your fuse settings allow non-root users:

```bash
sudo echo 'user_allow_other' >> /etc/fuse.conf"
```

Then use `pip` to install this repo:

```bash
pip install git+ssh://git@github.com/PressLabs/gitfs.git
```

## What's its purpose?

gitfs was designed to bring the full powers of git to everyone, no matter how
little they know about versioning. A user can mount any repository and all their 
changes will be automatically converted into commits. gitfs will also expose
the history of the branch you're currently working on by simulating snapshots of
every commit.

gitfs is useful in places where you want to keep track of all your files, but at
the same time you don't have the possibility of organizing everything into
commits yourself. A FUSE filesystem for git repositories, with local cache.

## Features
* Automatically commits changes: create, delete, update files and their metadata
* Browse through working index and commit history
* Merges with upstream by automatically accepting local changes
* Caching commits reduces the memory footprint and speeds up navigation
* Reduces the number of pushes by batching commits

## Development

You can find more documentation on [gitfs docs page](https://www.presslabs.com/help/gitfs/general).

### Contributing

Development of gitfs happens at http://github.com/PressLabs/gitfs.

Issues are tracked at http://github.com/PressLabs/gitfs/issues.

Python package can be found at https://pypi.python.org/pypi/gitfs/.

You are highly encouraged to contribute with code, tests, documentation or just
sharing experience.

Please see [CONTRIBUTING.md](CONTRIBUTING.md).

## License
This project is licensed under Apache 2.0 license. Read the [LICENSE](LICENSE) file in the
top distribution directory for the full license text.
