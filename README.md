dotfiles
========

<center><sub><sup>(click screenshot for a demo execution)</sup></sub></center>

[![](http://i.imgur.com/GafvUSe.png)](https://asciinema.org/a/98ssj3pm69zu39084ewfhktde)

[Bork](https://github.com/mattly/bork)-based dotfile setup for Mac and Linux systems that is really simple and easy to understand.

### Features

* Dotfile wrapper based on [Bork](https://github.com/mattly/bork) *ruff ruff*
    * Homebrew and Cask checks ensure that your packages / GUI apps are installed and up-to-date
    * Node `npm` package checks
    * Ruby `gem` package checks
    * Python `pip` package checks
    * [Atom](https://atom.io/) package checks
* [Vundle](https://github.com/gmarik/Vundle.vim) VIm plugin manager
* [Shell theme support](https://github.com/robbyrussell/oh-my-zsh/wiki/themes) for your prompts based on [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh/)
* Hostname specific configurations and customizations
* Fish-like auto autosuggestions in ZSH ([zsh-autosuggestions](https://github.com/tarruda/zsh-autosuggestions) plugin)
* Several preconfigured ZSH plugins:
    * [zsh-history-substring-search](https://github.com/zsh-users/zsh-history-substring-search) plugin
    * [zsh-notify](https://github.com/marzocchi/zsh-notify) plugin
    * [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-notify) plugin
    * [zsh-autosuggestions](https://github.com/tarruda/zsh-autosuggestions) plugin
    * [alias-tips](https://github.com/djui/alias-tips) plugin
* Configured GnuPG including `gpg-agent` and enabled commit signatures in git
* ~~Commented code, so you know what is actually going on~~ (Not anymore, to be honest...)

### Installation

1. Make sure to install homebrew and the following packages:  
  `brew install bork`
1. Fork this repository:  
  `git clone https://github.com/frdmn/dotfiles ~/.dotfiles`
1. Run the bootstrap script to initially install and setup the dotfiles:  
  `~/.dotfiles/dotfiles`

### Available commands

```sh
# Install/update the dotfiles
$ dotfiles

# Install/update one specific borkfile, located in borkfiles/
$ dotfiles <borkfile>
```

### Information

Explanation of the directories:

```
./bork
└── This folder includes the bork git repository which gets updated as
    soon as you update the the dotfiles.

./borkfiles
└── Includes the actual bork files, seperated to allow a condition based
    installation (system architecture, OS type).

./borkfiles/_.bork
└── This is the bootstrapping one, which applies the other Borkfiles in
    the same folder.

./configs
└── Contains all of your configuration files which gets symlinked into $HOME
    as ".$FILE". So basically, your actual dotfiles (zshrc, vimrc, gitconfig).

./configs/bash_vault
└── Secret stuff that you rather don't track in the git repo.

./hostnames
└── This folder could contain hostname specific (per host) configurations
    which gets processed during the execution of `dotfiles` if there is a
    folder that matches the current full (`hostname -f`) hostname.
./hostnames/example.hostna.me/borkfiles
└── If this folder contains brokfiles (files ending in ".bork"), they are
    getting executed during the `dotfiles` process.
./hostnames/example.hostna.me/configs
└── This folder could contain custom dotfile configurations that you only
    need on one specific host. A custom `.vimrc`? Just drop a file called
    `vimrc` in here and you are good to go. (If there is already a global one
    from ./configs with the same name, it will overwrite the global one).
./hostnames/example.hostna.me/includes
└── Dotfiles which get sourced by your Bash/ZSH shell on each login.

./opt
└── Specific files which gets symlinked into non-$HOME folders. Used by
    atom.bork.

./zsh
└── ZSH dependencies and plugins like the prompt, the zsh-syntax-highlighting.
    This folder gets symlinked into $HOME/.zsh and is used in ./configs/zshrc.
```

### Credits

* [Kasperisager](https://github.com/kasperisager), for the idea with Bork
* [Robby Russell](https://github.com/robbyrussell), for oh-my-zsh's theme support

### License

[MIT](LICENSE)

### Version

1.0
