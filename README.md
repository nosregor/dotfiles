# Setup instructions

You will find below the instructions for MacOS setup.

Please **read them carefully and execute all commands in the following order**.

Let's start 🚀

1. [Command line tools](#command-line-tools)
2.  [Prepare zsh install](#prepare-zsh-install)
3. [Full installation](#full-installation)

## Command line Tools

Open a new terminal, copy-paste the following command and hit `Enter`:

```bash
xcode-select --install
```

If you receive the following message, you can just skip this step and go to next step.

```bash
# command line tools are already installed, use "Software Update" to install updates
```

Otherwise, it will open a window asking you if you want to install some software: click on "Install" and wait.

![Install xcode-select on macOS](images/macos_xcode_select_install.png)

✅ If you see the message "The software was installed" then all good 👍

❌ If the command `xcode-select --install` fails try again: sometimes the Apple servers are overloaded.

❌ If you see the message "Xcode is not currently available from the Software Update server", you need to update the software update catalog:

```bash
sudo softwareupdate --clear-catalog
```

Once this is done, you can try to install again.

## Prepare zsh install

From inside this repo, run

```bash
$ .prepare-zsh-install.sh
$ exec zsh
```

This will install:

- [Homebrew](#homebrew)
- [zsh](#zsh)
- [Oh-my-zsh](#oh-my-zsh)

### Homebrew

[Homebrew](http://brew.sh/) is a package manager: it's a software used to install other software from the command line. Let's install it!

This will ask for your confirmation (hit `Enter`) and your **macOS user account password** (the one you use to [log in](https://support.apple.com/en-gb/HT202860) when you reboot your Macbook).

:warning: When you type your password, nothing will show up on the screen, **that's normal**. This is a security feature to mask not only your password as a whole but also its length. Just type your password and when you're done, press `Enter`.

:warning: If you see this warning 👇, run the two commands in the `Next steps` section to add Homebrew to your PATH:

![macOS Homebrew installation warning](images/macos_homebrew_warning.png)

```bash
# ⚠️ Only execute these commands if you saw this warning ☝
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

If you already have Homebrew, it will tell you so, that's fine, go on.

Then install some useful software:

```bash
brew update
```

If you get a `/usr/local must be writable` error, just run this:

```bash
sudo chown -R $USER:admin /usr/local
```

```bash
brew update
```

### zsh

Installs [Zsh](https://www.zsh.org/) homebrew formulae.

### Oh-my-zsh

Installs the `zsh` plugin [Oh My Zsh](https://ohmyz.sh/).

If asked "Do you want to change your default shell to zsh?", press `Y`

At the end your terminal should look like this:

![Ubuntu terminal with OhMyZsh](images/oh_my_zsh.png)

✅ If it does, you can continue 👍

## Full installation

In [functions](./zsh/.functions) you can run/rerun/modify the configuration.

```bash
$ setup_dotfiles # idempotent, can be executed after every `git pull`
```

Add/edit settings for alacritty, git, iterm2, nvim, VSCode, tmux, yabai and skhd in [config](./config/).

### Live Share configuration

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) is a VS Code extension which allows you to share the code in your text editor for debugging and pair-programming: let's set it up!

Launch VS Code from your terminal by typing `code` and pressing `Enter`.

Click on the little arrow at the bottom of the left bar 👇

![VS Code Live Share](images/vscode_live_share.png)

- Click on the "Share" button, then on "GitHub (Sign in using GitHub account)".
- A popup appears asking you to sign in with GitHub: click on "Allow".
- You are redirected to a GitHub page in you browser asking you to authorize Visual Studio Code: click on "Continue" then "Authorize github".
- VS Code may display additional pop-ups: close them by clicking "OK".

That's it, you're good to go!

## macOS Terminal Theme

Launch a terminal, click on `Terminal > Preferences` and set the "Pro" theme as default profile.

![Set Pro Theme for macOS terminal](images/macos_terminal_pro.png)

In Window tab, set also your **Window Size** to Columns: 200, Rows: 50

**Quit and restart** your terminal: it should now have a nice black background, easier on the eyes.
