.. image:: thumbnail.png

Ultimate Mac drop-down Quake-style terminal setup
=================================================
Below steps are in support of a YouTube video: link!!!!!

1. Install text editor. 
-----------------------
I prefer Visual Studio Code. Download and install on your machine from the `official web-site <https://code.visualstudio.com/download>`_

2. Create a .zshrc file
-----------------------
Look for .zshrc file in your home directory.
   
   .. note:: make sure to display hidden files with ``cmd+shift+.`` command. If you don't have .zshrc file in your home directory, create it with touch command in terminal.

.. code-block::

    touch ~/.zshrc

3. Install xcode developer tools.
----------------------------------
Required step for anything related to programming.

.. code-block::

    xcode-select --install
       
4. Install homebrew
-------------------
So-called missing package manager for MacOS or linux systems. It is just a convenient way to install many different development packages onto your machine.

For ARM macs
~~~~~~~~~~~~
.. code-block::
    
    cd ~/Downloads
    mkdir homebrew
    curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
    sudo mv homebrew /opt/homebrew
    export PATH="/opt/homebrew/bin:$PATH"

For intel macs
~~~~~~~~~~~~~~
.. code-block::
       
    cd ~/Downloads
    mkdir homebrew
    curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
    sudo mv homebrew /usr/local/homebrew
    export PATH="/usr/local/homebrew/bin:$PATH"

5. Install iTerm2
-----------------
Alternative to a built in Terminal, but it is far more configurable, which we need to get this look and feel of a drop down console.

.. code-block::

    brew install --cask iterm2

6. Install oh-my-zsh theme
--------------------------
This is a theme for a terminal, which will make it look nice and add some useful features.

.. code-block::

    sh -c "$(curl -fsLS https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

7. Configure path to brew in .zshrc file
-----------------------------------------
Add path to brew to your .zshrc file. Open it with your text editor and insert the following line at the end of the file:

For ARM macs
~~~~~~~~~~~~
    export PATH="/opt/homebrew/bin:$PATH"

For intel macs
~~~~~~~~~~~~~~
    export PATH="/usr/local/homebrew/bin:$PATH"


8. Install custom font
----------------------
 * In browser download font `here <https://github.com/Falkor/dotfiles/blob/master/fonts/SourceCodePro%2BPowerline%2BAwesome%2BRegular.ttf>`_
 * Open 'font book' on a mac (search 'font book' in spotlight) and drag&drop this font from downloads folder.

9. Install powerline10k theme
-----------------------------
This theme will help us configure iTerm2 to display information in a convenient way.

.. code-block::

    git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k

10. Configure iTerm2
-------------------
Working with iTerm2 settings.

 #. Delete default profile
    
    iTerm2 Settings -> Profiles -> create new profile, set as default, delete the 'Default' profile

    ::
        iTerm2 Settings
            Profiles
                create new profile
                set as Default
                delete Default Profile


 #. Configure colors

    Copy contents of danil.itermcolors file in this repo then create your own 'user.itermcolors' file in your home directory and paste the contents of danil.itermcolors file there.

    iTerm2 Settings -> Profiles -> Colors -> Color Presets -> Import (and chose this user.itermcolors file in the home dir) -> after import in Color Presets select this 'user' color theme

 #. Configure fonts

    iTerm2 Settings -> Profiles -> Text -> Font (find SourceCodePro+Powerline...) AND check the 'Use ligatures' checkbox AND increase fontsize to 14

 #. Statusbar

    iTerm2 Settings -> Profiles -> Session (check Status bar enabled) AND Configure Status Bar to display what you want. I use cpu + ram AND configure the Auto-Rainbow: Light Colors. Then select "Advanced" and change the background color (use color picker and pick color of iterm window)
    Then go to Settings -> Appearance and change the 'Status bar location' to 'Bottom'.

 #. Apply powerlevel10k

    Open .zshrc
     * replace the ``ZSH_THEME="robbyrussell"`` with ``ZSH_THEME="powerlevel10k/powerlevel10k"``
     * restart terminal and it will pop up with configuration wizard
     * answer ``(n)`` No to first (font) question
     * then logically to all other questions about icons appearance on the screen 
     * further settings are up to you, but the way I set it up in the video are as follows:
      * ``(3)`` Rainbow 
      * ``(1)`` Unicode 
      * ``(2)`` 24-hour format 
      * ``(1)`` Angled 
      * ``(1)`` Sharp 
      * ``(1)`` Flat 
      * ``(1)`` One Line 
      * ``(1)`` Compact 
      * ``(2)`` Many icons 
      * ``(1)`` Concise 
      * ``(y)`` Yes (Enable Transient Prompt) 
      * ``(1)`` Verbose 
      * ``(y)`` Yes (Overwrite ~/.p10k.zsh)
    You can always re-run this configuration by terminal command: p10k configure

1.  Plugins for terminal
------------------------
These will make life easier

Autosuggestion plugin
~~~~~~~~~~~~~~~~~~~~~~~~~
This plugin will add the command autosuggestion to terminal which user can use with 'tab'

.. code-block::

    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

Open .zshrc in the plugins variable (for now it should only include 'git') add zsh-autosuggestions !!! no comma between plugins in tuple.

syntax-highlighting
~~~~~~~~~~~~~~~~~~~~~~

.. code-block::

    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

Open .zshrc in the plugins variable add zsh-syntax-highlighting. At this step plugins variable should look like this: plugins=(git zsh-autosuggestions zsh-syntax-highlighting web-search)

Web-search from terminal with google command
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Open .zshrc and add web-search plugin to plugins variable: plugins=(git zsh-autosuggestions zsh-syntax-highlighting web-search)

12. Drop-down Quake-style mode
------------------------------
Configure shortcut 
~~~~~~~~~~~~~~~~~~
iTerm2 Settings -> Keys -> Hotkey -> Dedicated hotkey -> Ctrl+~ -> Check 'Floating Window'.

Further setup
~~~~~~~~~~~~~
    iTerm2 Settings -> Profiles -> Window -> 
        *Space* (All Spaces) 
        *Screen* (Screen with Cursor) 
        Check 'Hide after opening'

    In Profiles you will see a new profile *Hotkey Window* select it -> Window 
        Make sure 'Use transparrency' is checked 
        Change the 'Transparency' level to whatever suits you, I prefer 5

Open at computer startup
~~~~~~~~~~~~~~~~~~~~~~~~
With Spotlight open 'Login Items' and add iTerm2 to login items.
Remove it from dock and Tab-Switcher menu: iTerm2 Settings -> Appearance -> check Exclude from Dock...

This way it will always be available by the Ctrl+~ shortcut and if you need the settings, use 'Cmd+,' shortcut with console window opened

1.  Other useful settings
-------------------------
Open .zshrc and add: alias ll='ls -lG'
This enables an 'll' terminal command.

