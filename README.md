# My Config

Manage configuration files using Git.

## Initial setup

1. `git init $HOME/CFG`
   - Create a Git repository to track our configuration files
2. `alias config='/usr/bin/git --git-dir=$HOME/.cfg/.git/ --work-tree=$HOME'`
   - Create alias to run Git commands from outside of the configuration repository
   - Set working tree to `$HOME` allowing any file within the home folder to be added
3. `echo "alias config='/usr/bin/git --git-dir=$HOME/.cfg/.git/ --work-tree=$HOME'" >> $HOME/.zsh/aliases`
   - Make alias available permanently
4. `config config --local status.showUntrackedFiles no`
   - Only care about files we explicitly add to the repository

## Installation

1. `echo ".cfg" >> .gitignore`
   - Avoid recursive Git issues
2. `git clone git@github.com:manderegg/cfg.git $HOME/.cfg`
3. `alias config='/usr/bin/git --git-dir=$HOME/.cfg/.git/ --work-tree=$HOME'`
   - Bootstrap alias for current session until configuration setup complete
4. `config config --local status.showUntrackedFiles no`
   - Only care about files we explicitly add to the repository
5. Install [Oh My Zsh](https://ohmyz.sh/#install)
6. `brew bundle`
   - Install all packages from the `Brewfile`

## Usage

- Manage controlled configuration files using `config` in place of `git` e.g.
  - `config add {file}`
  - `config status`
  - `config commit -m "Added stuff"`
  - `config push origin`
- If possible, install pacakges via homebrew and update the `Brewfile`
  - `brew bundle dump` - recreates `Brewfile` in the current directory based on installed pacakges
    - NOTE: Need to delete existing file first, does not overwrite

## Credits

Based on the techniques described here:

- https://www.ackama.com/what-we-think/the-best-way-to-store-your-dotfiles-a-bare-git-repository-explained/
- https://www.atlassian.com/git/tutorials/dotfiles
- https://news.ycombinator.com/item?id=11071754
