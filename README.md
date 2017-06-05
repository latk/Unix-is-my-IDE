Unix is my IDE
==============

This repository contains a small collection of scripts that may be useful for command-line development on Linux.

Dependencies
------------

 -  Perl5, version 5.12 or better (tested with v5.24).

 -  GNU userland, in particular Bash and findutils. For example, we use non-POSIX compliant options for `xargs`. Pull Requests for other platforms welcome.

 -  The “standard” `file` implementation as commonly used on BSDs and Linux, not a POSIX-compliant substitute.

 -  The Ack search tool (https://beyondgrep.com/).

Installation
------------

Clone this repo, then set your PATH variable to point here. E.g. add this line to the end of your `~/.bashrc`:

    PATH="$PATH:~/path/to/unix-is-my-ide"

If you only want to use a single tool:

 - create a directory that is in your PATH, and from there point a symlink at the script you want to use.
 - add a shell alias for that script to your `~/.bashrc`.

Documentation
-------------

Each script contains a small help message. Either read the source code, or run it with the `--help` parameter to read usage information.

### find-todo

Finds TODO comments in your code.

This script searches through the given files for TODO comments.  A TODO comment
is any line that includes "TODO", "FIXME", or "XXX".  Yes, there will be false
positives.  For each occurrence, the location and context is printed and
color-highlighted.

To select which files are searched, you can specify command line arguments
which are then passed to ack-grep, so read the Ack docs for acceptable
flags. For example, `--perl` will only search Perl source files.

Example: search for to-do comments in all Perl source files found inside the "lib" folder:

    $ find-todo lib --perl

### find-vim-swapfiles

Find Vim swapfiles, and delete them if requested.

Example: list all swapfiles in the lib directory:

    $ find-vim-swapfiles lib

Example: delete all swapfiles under the current directory:

    $ find-vim-swapfiles --remove-all

### open-git-project

Start an editor with all tracked files in a Git repository.

The current working directory must be inside the working dir of a Git repo.
Then, an editor is launched with files that

 - are tracked by Git,
 - are under the current working directory, and
 - are text files, as determined by their MIME type.

The editor is determined by the `$EDITOR` environment variable, or can be specified on the command line. The command line may also include extra args for your editor, e.g. additional files you want to open. The editor must be able to process a list of files given on the command line.

Example: normal usage:

    $ open-git-project

Example: specifying an editor and extra files:

    $ open-git-project gvim newfile.txt ../other-file.txt

Stability Policy
----------------

None. Breaking changes may happen at any time. Consider pinning a version if you need stability.

Support
-------

If you find any bugs, open an issue on GitHub. Please explain:

 - what you did
 - what you expected to happen
 - what actually happened (e.g. please copy and paste any error messages)
 - relevant system configuration

If you can create a small test script to reproduce the error, that makes helping you a lot easier.

I'll try to acknowledge the issue within a week, but remember this is just a hobby project, so: no promises.

Contributing
------------

You are welcome to contribute via pull requests for

 - bug fixes and style improvements
 - better portability
 - better documentation
 - better features
 - additional scripts in a similar spirit

If you have an idea for new functionality, please open an issue first to discuss the topic.

Copyright
---------

Copyright 2017 Lukas Atkinson

Each script in this collection has its own license. See their source code for details. License index:

 - `find-todo`: GPLv3+
 - `find-vim-swapfile`: Apache License 2.0
 - `open-git-project`: Apache License 2.0
