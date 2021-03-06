# Vim.ana #

**Vim.ana** aims to make a 2-command install of a full vim IDE with CLI conveniences.  Think of Vim being able to do everything that can be done with IntelliJ, or similar.  

The focus of this repo is to be portable, environment-neutral, and safe for existing configs.  Vim.ana is a Vim & related environment that can be dropped into any unix-flavor box, and without disruption to existing production configs.

## Features ##
* Pathogen for loading.
* Familiar windowing setup of File Browser + Open Files + Edit Window.
* IDE features that align with RubyMine, Eclipse, and others.
* Comprehensive file and symbol search system


## Components ##

See the commented sections of [`.gitmodules`](https://github.com/NewAlexandria/vim.ana/blob/master/.gitmodules)
The submodules file is structured and commented, and wil provide a nice guide as to what's in the box.

   Loader, IDE, 'Windowing', Formatting, Syntax Colors

The `.vimrc` is [organized into logical sections](https://github.com/NewAlexandria/vim.ana/blob/master/.vim/plugin), with the `.vimrc` retainin jump-points to each.

1. To see a [list of all mappings](https://github.com/NewAlexandria/vim.ana#leader-and-unite-mappings) in the .vimrc group - type: `<leader>L` *(which should be `\L`)*
2. To see a list of all the mappings from plugings, vimrc, etc. - type: `:map`

**dbext**, the DB browser, [has a great tutorial, here](http://mutelight.org/dbext-the-last-sql-client-youll-ever-need)


## Install ##
**Vim 7.3 is recommended.  Some version greater than 7.0.23 is required for buffergator, unite, and possibly others.**

Download and unpack to `~/.vim.ana` (the installer will look for it here. You can move it later)

` cd ~; git clone git@github.com:NewAlexandria/vim.ana.git .vim.ana `

> If your corporate enterprise firewalls `ssh` to GitHub, then you can use this link
> 
> ` cd ~; git clone https://github.com/NewAlexandria/vim.ana.git .vim.ana `

then link files and [do some other business](https://github.com/NewAlexandria/vim.ana/blob/master/install.sh)

` .vim.ana/install.sh `

The installer responsibily makes backups of your original .vim files to ~/.vim.ana/backups/  You can safely uninstall the files if need be (unlike if I'd `cp -R` the lot into your existing `.vim`)

The submodule bundles are automatically pulled down.

### Ctags ###

You'll want to remember to install [the *ctags* library](http://ctags.sourceforge.net/).  Installation strategies differ per-platform, and I wanted the `install.sh` to be robust.  If you're on OS X, you can ``brew install ctags``

* The out-of-the-box ctags installation does not seem to handle anon functions in `.js` files, and barfs to stdout.  [See my `.dotfiles` solution to this](https://github.com/NewAlexandria/dotfiles/blob/master/ctags)
* Ensure ctags reach into the gems installed in your rails app: [use Tim Pope's excellent gem-ctags](https://github.com/tpope/gem-ctags#installation)
* Also consider [ctag-indexing those Ruby stlibs](https://github.com/tpope/rbenv-ctags#installation), too.
* Be aware that, with `rspec`, your [describe blocks may not be correctly indexed](https://github.com/fishman/ctags/issues/11), even with [fishman's ctag build](https://github.com/fishman/ctags) for Ruby methods


### OSX Users ###

The pre-insintalled `Vim` does not come compiled with `lua`.  See [Chris' awesome instructions](http://www.codeography.com/2013/06/11/install-macvim-with-lua-support.html) for compiling Vim and MacVim with homebrew.

That's it for now.

## Customization ##

If you want to add your own plugins, note that this repo uses git submodules:

Additions: `cd ~/.vim.ana; git submodule add git-repo-address .vim/bundles/name-of-repo`
Removals:  `cd ~/.vim.ana; git submodule deinit .vim/bundles/name-of-repo` then edit the `.gitmodules` file to remove the entry.

### Think Submodules are teh stank? ###
They *used* to be, before `deinit`. [See the talk, here](http://stackoverflow.com/questions/1260748/how-do-i-remove-a-git-submodule)


## Mañana ##

The following directions are under review:

- adding a Unite scope for `dbext` databases (or [SQLcomplete](https://github.com/vim-scripts/SQLComplete.vim))
- VCSCommand
- netrw
- a proper tag parses for ruby *and rspec* namespaces, since 'ctags' fails at this, perhaps [starscope](https://github.com/eapache/starscope/blob/master/doc/USER_GUIDE.md),  [tagfinder](http://andrewradev.com/2011/10/15/vim-and-ctags-finding-tag-definitions/), or [rdoc-tags](https://github.com/rdoc/rdoc-tags)
- A clear winner for ctag support, whether tpope's, [vim-tags](https://github.com/szw/vim-tags), or another.
- Install via [Vimswitch](https://priomsrb.github.io/vimswitch/)?
- [configure for Tmux](http://tilvim.com/2014/07/30/tmux-and-vim.html)


# Спасибо #

Thanks for experimenting with this repo.  Suggestions always welcome. I'm particularly interested in 

* A new way to onbaord people into using the features of this configuration. (Recent `LeaderMap()` function was the start)
* How this can more-safely integrate with your existing environment practices (this may be Vimswitch)
* How to lower the version dependecy with Vim
* How to integrate with windowing apps on all platforms
* How to get the lauch time near-instant (takes as much as 1.5 sec on slow slices)

## Sauce ##

#### Windowing Layout
![The awesomeness you'll get with this repo](http://i.imgur.com/p262L.png)

#### Leader and Unite Mappings
![the LeaderMap() function](http://i.imgur.com/4InDFSt.png)
[See the function](https://github.com/NewAlexandria/vim.ana/blob/master/.vim/plugin/ide.rc.vim#L51)

