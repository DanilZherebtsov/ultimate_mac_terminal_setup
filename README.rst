* Guide for setting up ultimate Mac drop-down Quake-style terminal
# in support of a YouTube video: link!!!!!

**1. Install xcode developer tools.

.. code-block::
   :caption: in terminal

    xcode-select --install
       

**2. Install homebrew

.. code-block::
   :caption: in terminal

    cd ~/Downloads
    mkdir homebrew
    curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
    sudo mv homebrew /opt/homebrew

**3. Install iTerm2

Next up install iTerm2 - this is an alternative to a built in Terminal, but it is far more configurable, which we need to get this look and feel of a drop down console.

.. code-block::
   :caption: in terminal

    brew install --cask iterm2

Now to make it prettier - install oh-my-zsh theme. And this will affect all the terminals (builtin, iterm2, vscode terminal, and any other command line tool on your machine)

```markdown
# install oh-my-zsh (theme) - 
    sh -c "$(curl -fsLS https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

Install font to make it prettier
  in browser download font from here:   https://github.com/Falkor/dotfiles/blob/master/fonts/SourceCodePro%2BPowerline%2BAwesome%2BRegular.ttf
  then open 'font book' with spotlight and drag&drop this font from downloads folder

install iterm2 theme powerlevel10k which will help us configure iterm to display information efficiently.
    git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k

Now let’s go into iterm2 settings and configure everything that is left.

Delete default profile

# in iterm2 -> Settings -> Profiles -> create new profile, set as default, delete the 'Default' profile

setup colors
# my color map preset is here (just copy the contents of danil.itermcolors file: !!! LINK TO GITHUB REPO FILE ) then save this create your own 'user.itermcolors' file in your home directory and paste the contents of danil.itermcolors file there.
# this can be done through terminal (when in home dir):
    code danil.itermcolors # this will create this file in home dir
    # and paste the contents of the danil.itermcolors from github
# then go to iterm2 -> Settings -> Profiles -> Colors -> Color Presets -> Import (and chose this danil.itermcolors file in the home dir) -> after import in Color Presets select this 'danil' color theme

Fonts
# font: Profiles -> Text -> Font (find SourceCodePro+Powerline...) AND check the 'Use ligatures' checkbox AND increase fontsize to 14

Statusbar
# statusbar: Profiles -> Session (check Status bar enabled) AND Configure Status Bar to display what you want. I use cpu + ram AND configure the Auto-Rainbow: Light Colors. Then select "Advanced" and change the background color (use color picker and pick color of iterm window)
# then go to Settings -> Appearance and change the 'Status bar location' to 'Bottom'

# set the downloaded theme powerlevel10k that we downloaded
    code .zshrc
# and replace the ZSH_THEME="robbyrussell" with ZSH_THEME="powerlevel10k/powerlevel10k"
# restart and it will pop up with configuration wizard: answer No to first (font) question then logically to all other questions about icons appearance on the screen -> Rainbow -> Unicode -> 24-hour format -> Angled -> Sharp -> Flat -> One Line -> Compact -> Many icons -> Concise -> Verbose -> Yes
# you can always re-run this configuration by terminal command: p10k configure

PLUGINS
# install autosuggestion plugin
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
# in .zshrc in the plugins variable (for now it should only include 'git') add zsh-autosuggestions !!! no comma between plugins in tuple.

# syntax-highlighting
    https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
# in .zshrc in the plugins variable (for now it should only include 'git') add zsh-syntax-highlighting !!! no comma between plugins in tuple.

# web-search from terminal with google command
# just add in .zshrc plugins(web-search)

Drop-down mode
# configure shortcut Settings -> Keys -> Hotkey -> Dedicated hotkey -> Ctrl+~ -> Check 'Floating Window'.
# then go to Profiles -> Window -> Space (All Spaces) AND Screen (Screen with Cursor) AND set Transparrency to 5 AND check 'Hide after opening'
# Now set it to run every time you boot up your mac:
# with Spotlight -> Users & Groups and add iTerm2 to login items
# and remove it from dock and Tab-Switcher menu: Settings -> Appearance -> check Exclude from Dock...
# This way it will always be available by the Ctrl+~ shortcut and if you need the settings, use Cmd+, shortcut with console window opened

# to remove yellow folder highlighting
    chmod go-w
# ------------------------------------------------------------------------------------------

# OTHER .zshrc settings
# ll terminal command
    alias ll='ls -lG'
