# cosmere-terminal (with neofetch and fortune).

A linux terminal tool that displays a random ASCII cosmere related image alongside a random cosmere quote on terminal startup.


## acknowledgements.

 - [neofetch](https://github.com/dylanaraps/neofetch) : most used tool for linux ricing.
 - [fortune-mod](https://github.com/shlomif/fortune-mod) : utility that print a random quote from a predefined list.
 - [ascii-image-converter](https://github.com/TheZoraiz/ascii-image-converter) : a great tool to convert from image to ASCII. Used because of the great level of detail that can be achieved with it.


## installation

First of all for this to work you'll need to install:

- neofetch.

- fortune.


### fortune:
Once you have that sorted out you can continue by cloning this repo in any location you want.

You will notice two files called ``` cosmerequotes ```: one will be a .txt file and the other a .dat. These are necessary for fortune to print out the quotes. Fortune has a folder (tipically ``` /usr/share/fortune ```) where stores all of its quotes in different categories.

We want our cosmere quotes stored there too. For that we will use: 

```bash
  cp cosmerequotes /usr/share/fortune/
  cp cosmerequotes.dat /usr/share/fortune/

```
This allows fortune to access these quotes from wherever in our system.

If we wish to modify the file to add or substract quotes we will do it in the .txt file, where we will notice that each quotes its separated by '%' and the last line of text its blank. Once our modifications are done, we have to run:

```bash
  strfile -c % cosmerequotes cosmerequotes.dat
  cp cosmerequotes /usr/share/fortune/
  cp cosmerequotes.dat /usr/share/fortune/
```

The changes should be visible now. This has to be done after every modification.

### neofetch:

For neofetch we will need to comment the info displayed. For this we should modify a ```.config.conf``` file inside ``` /home/username/.config/neofetch/ ``` . Something similar to this should be fine:

```bash
    # info title
    info underline

    # info "OS" distro
    # info "Host" model
    # info "Kernel" kernel
    # info "Uptime" uptime
    # info "Packages" packages
    # info "Shell" shell
    # info "Resolution" resolution
    # info "DE" de
    # info "WM" wm
    # info "WM Theme" wm_theme
    # info "Theme" theme
    # info "Icons" icons
    # info "Terminal" term
    # info "Terminal Font" term_font
    # info "CPU" cpu
    # info "GPU" gpu
    # info "Memory" memory
```

After this we are done with neofetch.

### implementing all on terminal startup:

Locate the file that executes on terminal startup, in my case its ``` .zshrc ``` because im using ohmyzsh. Your could be ``` .bashrc ```. Open it with a text editor and add this line at the end of file:

``` neofetch --ascii "$(find /path/to/ascii/folder -name '*.txt' | shuf -n 1)" && fortune cosmerequotes ```

Save and exit. Know your terminal should display an ASCII and a quote on startup :-).
## Screenshots

![App Screenshot](https://i.imgur.com/f4RDtTv.png)

