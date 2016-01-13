myNvim
=====

A script that creates a portable bundle of your Neovim environment.

Usage
-----

`myNvim` script will create an executable named `nvim.$(whoami)`.

```sh
bash <(curl -fL https://raw.githubusercontent.com/alok/myNvim/master/myNvim)
```

### Options

- `-e|--edit`
    - Allow you to edit the list of files to be archived and the environment
      variables to apply
- `-j`
    - Use bzip2 instead of gzip
- `--exclude PATTERN`
    - `grep -v` pattern for excluding files

Why?
----

You want your Neovim settings and plugins on whichever server you connect to. But
having your .vimrc on GitHub or Bitbucket is usually not enough. Because:

- You need Git and free access to internet
- Even when both conditions are met, downloading plugins can be time-consuming
- When the user account on the server is shared among coworkers, you need to
  restore the default configuration every time when you're done

How does it work?
-----------------

`myNvim` creates a tar archive of your .vimrc and .vim directory and append it
to a small bash script that starts Neovim with your usual settings and plugins.

Caveat
------

The generated script injects code for temporarily swapping `$HOME` variable
around the vimrc in the archive. This is because most vimrcs contain
references to home directory (e.g. `call plug#begin('~/.vim/plugged')`).


### NOTE
Neovim must be installed on your remote machine, else this will not work.
