Cleany
======

> A wrapper script for Geany projects.

---

Introduction
------------

`cleany` is a simple Bash wrapper script around Geany's executable which
makes it easier to open projects. Every project gets its own
complete configuration (both global and project-specific). Geany is
started up in a mode suitable for working on a project as a directory
of files.

Other than `-h` for help/usage message, only the last argument passed
to `cleany` is processed, the rest of the arguments are passed directly
to `geany`. The last argument is taken to be the project base directory.
If the project doesn't exist, a new configuration will be created for it.

`cleany` passes a project-specific configuration directory using the `-c`
option as well as passes a project filename to Geany.

----

Usage
-----

#### Create or open project in the current directory

`$ cleany .`

#### Create or open a project in another directory

`$ cleany /else/where`

---

Tips
----

  - Add the `cleany` script to your `$PATH` environment variable to
    avoid having to type its full path.
  - Load the "ProjectOrganizer" plugin to get project-wide tags and
    a sidebar tree to navigate the project.
  - Add `.geany` to your version control system's exclude list.
    - Ex. put `/.geany/` in `.gitignore` file for Git VCS.

----

Bugs
----

  - Geany seems to clobber rather than honour the `last_dir` value in
    the `[VTE]` group of the initial project file. I would expect it to
    change directories in the Terminal to this directory, if specified.
  - There's probably all kinds of command-line arguments that will
    be confused between this wrapper script and Geany itself. The above
    usage examples should be fine, however.

----

Default directory structure
---------------------------

Below is an example of the resulting files on a fresh `cleany` project
directory:

```bash
$ cleany foo
$ tree -a foo
foo
└── .geany
    ├── config
    │   ├── filedefs
    │   │   └── filetypes.README
    │   ├── geany.conf
    │   ├── keybindings.conf
    │   └── templates
    │       ├── files
    │       └── templates.README
    └── foo.geany

5 directories, 5 files
```
