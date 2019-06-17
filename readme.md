# 🌊 Pipeline for Mac

![pipeline](./pipeline.jpg)

Rad setup scripts to prepare your Mac for development. Installs
[Homebrew][homebrew], [Git][git], [Oh My Zsh][oh-my-zsh], [nodenv][nodenv],
and a 💅 stylin [terminal theme][zsh-bullet-train]. Installs the bare-minimum
to get you up-and running without slowing you down. Afterwards you can
customize anything added (see FAQ below), or install any additional packages
you need.

## 🏄 Features

| Name                                       | What is it?                                                                                                                                                                                                               |
| :----------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Xcode Tools                                | Utilities needed for most programs, without the weight of full [Xcode][xcode]. This tiny install is needed for most other utilities you need.                                                                             |
| [Homebrew][homebrew]                       | THE package manager for Mac. Lets you install & uninstall software quickly, painlessly, and without putting your system in danger.                                                                                        |
| [Git][git]                                 | Standard version control for modern software. Enables teams to work collaboratively and keep backups of all historic code changes.                                                                                        |
| [Nodenv][nodenv]                           | Multiple projects require different [Node.js][node] versions. Nodenv lets you effortlessly switch between Node.js versions, or fall back to your preferred default version if none is specified. Simpler to use than NVM. |
| [Oh My Zsh][oh-my-zsh]                     | Get an awesome shell without copying + pasting shell scripts willy-nilly. Plugins, themes, and a community make shell customization fun!                                                                                  |
| [The Silver Searcher][the-silver-searcher] | Search contents of all files on your system faster than… well… just about anything else.                                                                                                                                  |

### What’s not included

The following dev tools aren’t installed by this script, but thanks to
Homebrew can be optionally installed after finishing:

| Name                 | Command                                                    |
| :------------------- | :--------------------------------------------------------- |
| [Golang][golang]     | `brew install go`                                          |
| [PHPBrew][phpbrew]   | None; follow [instructions][phpbrew]                       |
| [Postgres][postgres] | `brew install postgres`                                    |
| [rbenv][rbenv]       | `brew install rbenv` (read the post-install setup message) |

## 🚀 Running the script

It’s important to view the [source][source] before installing any script.

```bash
sh -c "$(curl -s https://raw.githubusercontent.com/dangodev/pipeline/master/bin/pipeline)"
```

### Post-setup

Change the font in your terminal to the newly-installed “Perplexed” font in
order for the icons to work correctly. Many terminals don’t allow changing
this via the shell, so this is a manual change.

✨Also grab an awesome terminal background from
[here][awesome-terminal-backgrounds].

### …Now what?

Okay, it’s installed… now what can I do?

#### Commands

| Command                         | What it does                                                                                                                     |
| :------------------------------ | :------------------------------------------------------------------------------------------------------------------------------- |
| (start typing)                  | Your shell will now highlight correct commands in **green**, incorrect ones in **red**—before you hit <kbd>Enter</kbd>!          |
| (start typing) + <kbd>tab</kbd> | Start typing any command, and hit <kbd>tab</kbd>. Your shell will try and complete it for you!                                   |
| `z [my-folder]`                 | Jump quickly from any folder to another, by typing its name (_note: `cd` into it first_)                                         |
| `ag myFunction ~/code`          | Search all files in `~/code` containing `myFunction` using [The Silver Searcher][the-silver-searcher]. Blazing-fast 🔥           |
| `gl`                            | `git pull --rebase` Update branch with origin                                                                                    |
| `gpf`                           | `git push --force --force-with-lease` Force-push but fail if something changed remotely (great for ninja edits without the risk) |
| `grc`                           | `git rebase --continue` If rebasing through a conflict, continue                                                                 |
| `grm`                           | `git rebase -i origin/master` Rebase current branch from master                                                                  |

#### Speed Tips

- **Manage Node with ease.** Add a `.node-version` file in any folder with
  `12.4.0` (or any node version). Now whenever you’re in that folder,
  [nodenv][nodenv] will automatically switch the Node version for you 🎉 (if
  you’re missing that version, just run `nodenv install [version]`).
- **Ditch editor projects.** If you use VS Code, install the `code` command
  (<kbd>⌘</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>, type `code`). Now you can
  jump between projects with `z project1 && code .` and `z project2 && code .`

#### FAQ

##### I don’t have a cool gradient background! How do I get one?

Alas, terminal backgrounds (along with fonts) are something this script
cannot do. But good news! You can find many great backgrounds at [✨
awesome-terminal-backgrounds][awesome-terminal-backgrounds].

##### How can I recolor or reorder the terminal segments?

The theme installed, [Bullet Train][bullet-train], was actually made for
this! In your `.zshrc` file, you’ll see the following lines:

```
prompt_emoji() {
  prompt_segment black white "✨"
}
BULLETTRAIN_PROMPT_ORDER=(emoji status dir nvm git)
BULLETTRAIN_PROMPT_ADD_NEWLINE=false
BULLETTRAIN_PROMPT_CHAR=""
BULLETTRAIN_DIR_BG=magenta
BULLETTRAIN_DIR_FG=black
BULLETTRAIN_GIT_BG=green
BULLETTRAIN_GIT_COLORIZE_DIRTY=true
BULLETTRAIN_GIT_EXTENDED=false
BULLETTRAIN_GIT_FG=black
BULLETTRAIN_NVM_BG=black
BULLETTRAIN_NVM_FG=green
BULLETTRAIN_NVM_SHOW=true
```

Edit `BULLETTRAIN_PROMPT_ORDER` to change the ordering, and you can use the
settings below to alter their foreground & background colors. You use add
segments for Ruby, Kubernetes, Go, and it even allows for custom segments as
well. Consult [the docs][bullet-train] to learn how.

If you’d like to try another theme altogether, Oh My Zsh has [quite a few
built-in themes][oh-my-zsh-theme], as well as a wide selection of
[third-party ones][oh-my-zsh-external].

##### I’m seeing weird symbols in my terminal. Is that normal?

You probably need to change your font to “Perplexed,” a patched version of
IBM Sans with built-in icons for your terminal.

##### I don’t like the terminal font. Can I change it?

You can install any font with modified special characters (needed for the
icons in terminal). You can find such fonts here:

- [Nerd Fonts][nerd-fonts]
- [Powerline Fonts][powerline-fonts]

In case you don’t like IBM Plex Sans (my personal preference), `Hack`, `Input Mono`, and `Meslo` (the default Mac font, but patched with icons) are also
great.

Once installed, change your terminal preferences to use the modified font.

## Uninstalling

There’s not an uninstall script, but the changes this script makes are easy
to undo:

| Change                           | Uninstalling                                                                                                                                                                                                                                    |
| :------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Xcode tools                      | [Uninstall][xcode-uninstall] but I wouldn’t recommend it as this should be part of your system. Many tools will just re-install this anyway; this is only missing sometimes on brand-new systems but usually gets installed one way or another. |
| Homebrew                         | [Uninstall][homebrew-uninstall]                                                                                                                                                                                                                 |
| Oh My Zsh                        | [Uninstall][oh-my-zsh-uninstall] (note that this will also remove plugins & theme changes as well)                                                                                                                                              |
| `~/.hushlogin`                   | This hides the annoying ”Last login” message on every terminal bootup. Delete this empty file to undo it.                                                                                                                                       |
| `~/Library/Perplexed-Normal.otf` | 1 font was installed for your convenience. Uninstall “Perplexed Normal” via Font Book, or delete this file.                                                                                                                                     |
| `~/.zshrc`                       | Oh My Zsh will leave this around, in case you want to use zsh without it. Delete this file if you wish to return to Bash.                                                                                                                       |

That’s it! No other files or system settings were affected.

## ️🤷🏻‍♂️ About

I’m Drew, and I’ve been designing & building UI for over a decade. I also
appreciate pretty things ✨. This script came about from several people over
the years asking me [about my config][config], and to set up their machines.
I had more than 3 people ask, so I automated it 🤖.

This setup is one of the least-opinionated setups I’ve come across, but that
also doesn’t mean it’s for everyone. This tool is for people that either
don’t have experience customizing their tooling, or don’t want to.

This software is **public domain**. Remix, copy, steal, whatever—just use it
to help others! Use at your own risk.

### Inspiration

- [Laptop][laptop] by thoughtbot
- [Formation][formation] by Mina Markham

[awesome-terminal-backgrounds]: https://github.com/dangodev/awesome-terminal-backgrounds
[bullet-train]: https://github.com/caiogondim/bullet-train.zsh
[config]: https://github.com/dangodev/config
[formation]: https://github.com/minamarkham/formation
[git]: https://git-scm.com/
[golang]: https://golang.org/
[homebrew]: https://brew.sh/
[homebrew-uninstall]: https://docs.brew.sh/FAQ#how-do-i-uninstall-homebrew
[iterm]: https://www.iterm2.com
[laptop]: https://github.com/thoughtbot/laptop
[mit]: https://opensource.org/licenses/MIT
[nerd-fonts]: https://github.com/ryanoasis/nerd-fonts
[node]: https://nodejs.org/en/
[nodenv]: https://github.com/nodenv/nodenv
[oh-my-zsh]: https://github.com/robbyrussell/oh-my-zsh
[oh-my-zsh-external]: https://github.com/robbyrussell/oh-my-zsh/wiki/External-themes
[oh-my-zsh-theme]: https://github.com/robbyrussell/oh-my-zsh/wiki/Themes
[oh-my-zsh-uninstall]: https://github.com/robbyrussell/oh-my-zsh#uninstalling-oh-my-zsh
[perplexed]: https://github.com/phoikoi/perplexed
[phpbrew]: https://github.com/phpbrew/phpbrew
[postgres]: https://www.postgresql.org/
[powerline-fonts]: https://github.com/powerline/fonts
[rbenv]: https://github.com/rbenv/rbenv
[source]: ./bin/pipeline
[the-silver-searcher]: https://github.com/ggreer/the_silver_searcher
[xcode]: https://developer.apple.com/xcode/
[xcode-uninstall]: https://developer.apple.com/library/archive/technotes/tn2339/_index.html#//apple_ref/doc/uid/DTS40014588-CH1-HOW_CAN_I_UNINSTALL_THE_COMMAND_LINE_TOOLS_
[zsh-bullet-train]: https://github.com/caiogondim/bullet-train.zsh
