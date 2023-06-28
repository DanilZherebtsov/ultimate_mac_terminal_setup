.. image:: thumbnail.png

Ultimate Mac drop-down Quake-style terminal setup
=================================================
Below steps are in support of a YouTube video: link!!!!!

1. Install text editor
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

If you don't have git on your machine, install it with brew:

.. code-block::

    brew install git

10.  Configure iTerm2
-------------------
Working with iTerm2 settings.

 #. Delete default profile
  
        Settings
            Profiles
                create new profile
                set as Default
                delete Default Profile


 #. Configure colors

    Copy contents of danil.itermcolors file in this repo then create your own 'user.itermcolors' file in your home directory and paste the contents of danil.itermcolors file there. Then in iTerm2 go to:

        Settings
            Profiles
                Colors
                    Color Presets
                        in ``Color Presets`` drop-down menu select ``Import`` (and select this user.itermcolors file in the home dir)
                        
                        after import in ``Color Presets`` drop-down menu select this 'user' color theme

 #. Configure fonts

    Settings
        Profiles
            Text
                Font 
                    find ``SourceCodePro+Powerline...``
                    
                    check the ``Use ligatures`` checkbox
                    
                    increase fontsize to 14

 #. Statusbar

    Settings
        Profiles
            Session 
                check ``Status bar enabled``                 
                select ``Configure Status Bar`` 
                    Configure what you want to display by dragging the modules down, I use the following:
                    
                        CPU
                        
                        RAM
                        
                        Auto-Rainbow -> Light Colors
                        
                        Select ``Advanced``
                            change the background color (use color picker and pick color of iterm window)
    Settings
        Appearance
            change the ``Status bar location`` to 'Bottom'.

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

11.  Plugins for terminal
------------------------
Minor things that are very convenient

 #. Autosuggestion plugin
    This plugin will add the command autosuggestion to terminal which user can use with 'tab'

    .. code-block::

        git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

    Open .zshrc and in the plugins variable (for now it should look like this ``plugins=(git)``). Add zsh-autosuggestions (!!! no comma between plugins in tuple). The result shoud look like this: ``plugins=(git zsh-autosuggestions)``

 #. syntax-highlighting
    This plugin will highlight syntax in terminal
    .. code-block::

        git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

    Open .zshrc and in the plugins variable add zsh-syntax-highlighting. At this step plugins variable should look like this: ``plugins=(git zsh-autosuggestions zsh-syntax-highlighting)``

 #. Web-search from terminal with google command
    This will allow useing terminal to search google

    Open .zshrc and and add ``web-search`` to plugins variable. Now your plugins will look like this ``plugins=(git zsh-autosuggestions zsh-syntax-highlighting web-search)``

12.  Drop-down Quake-style mode
------------------------------
#. Configure shortcut 

    Settings
        Keys
            Hotkey
                select ``Create a Dedicated Hotkey Window``
                
                    input your hotkey ``Ctrl+~``
                
                    check ``Floating Window``

 #. Further setup

    Settings
        Profiles
            Window        
                in the ``Space`` drop-down menu select ``All Spaces``
                
                in the ``Screen`` drop-down menu select ``Screen with Cursor``
        
                check ``Hide after opening``

    In Profiles you will see a new profile ``Hotkey Window`` select it
        Window             
            Make sure ``Use transparrency`` is checked 
        
            Change the ``Transparency`` level to whatever suits you, I prefer 5

 #. Open iTerm2 and hide it at computer startup

    With Spotlight open **Login Items** and add iTerm2 to login items

    Remove it from dock and Tab-Switcher menu: 
    
        Settings
            Appearance            
                check ``Exclude from Dock and Tab Application Switcher``

    Now your terminal will be allways be running in the background and regardless of which screen you are on you can toggle pull it down/up with ``Ctrl+~`` shortcut
    
    If you need the settings, use ``Cmd+,``` shortcut when terminal window is on screen

13. Configure VSCode
--------------------

 #. Support the custom font in VSCode terminal
    
    Go to VSCode settings and search for ``terminal.integrated.fontFamily`` and paste there ``'SourceCodePro+Powerline+Awesome Regular'`` (**make sure to use quotes**)

 #. Configure launching VSCode with terminal ``code`` command

    Add this line to your .zshrc file

    ``code () { VSCODE_CWD="$PWD" open -n -b "com.microsoft.VSCode" --args $* ;}``