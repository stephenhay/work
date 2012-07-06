work
====

A very simple command line time tracker

I made this for personal use and to practice some shell scripting. It is incomplete and full of bugs and things that can (and perhaps will) be improved. Thus, **use at your own risk**. I have no timeline for completion of this; I just keep adding and adjusting as I need to for my own purposes.

`work` is written in bash, and utilizes some standard unix tools available on OS X and several other platforms, such as `date` and `awk`, among others. Please note that `date` can work differently depending on your platform and you may have to change the functions which use `date` depending on your required syntax.

## Installation

Place `work` in your `$PATH`. Make sure it's executable.

## Configuration

You can change the location of the entry file and backup file by modifying `work` with your favorite text editor.

    #config
    file=~/.work.csv
    backupfile=~/backups/work.csv

## Usage
work is very simple to use:

    work on "Whatever it is that you're going to do" project.optional_subproject

when you want to begin a task. The quotes around the task are necessary. Spaces are not allowed in the project name.

When you stop working on the task:

    work done

Entries are added to `.work.csv`. Yes, CSV, not JSON or YAML or whatever. Maybe later. At the end of each entry, a time total for that specific task is added and rounded to the nearest 15 minutes. This can be useful when generating reports.

If you forget to make an entry, or are not at the computer and need to add an entry after the fact, then you need to add the entire entry manually. You can do this by editing `.work.csv`, which is easy enough, but you may also use `catchup`:

    work catchup

The script will respond:

    Please make an entry with the format 'project,task,yyyy-mm-dd hh:mm,yyyy-mm-dd hh:mm,[x] hr [y] min':

Type in your entry and hit return. The script will re-sort the file to put your entry where it belongs.

`work.csv` is a plain text file, so it's easy enough to find entries with simple search in your text editor or with `grep`. However, you can do a simple `grep` and `sort` by doing:

    work find [keyword]

where `[keyword]` is the word or fragment you're searching for. This is equivalent to `grep [keyword] work.csv | sort`.

To get a list of projects, do:

    work projects

## Tentative plans

Plain text is fantastic, and there's a lot that can be done with such a straightforward text file. Obviously, I plan on writing some simple reports filtered by date range and/or project. I also plan on doing error handling, because there is literally **none** right now. Basically, this script is a quick hack which creates a text file which is very useful for my purposes. As I have the time I hope to fix it up in case other people might find it useful.

## Author

`work` is written by Stephen Hay, and is released under the MIT license.
