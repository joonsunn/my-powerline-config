# Steps taken to install powerline

Following instructions from this youtube video: <https://www.youtube.com/watch?v=zfm2E4E7Dok>

#### 1. Check python installed

```bash
python3 --version
```

#### 2. Check pip3 installed

```bash
pip3
```

If pip3 not installed, run command as displayed in terminal, or:

```bash
sudo apt install python3-pip
```

#### 3. Install powerline

```bash
pip3 install --user powerline-status
```

#### 4. Install powerline git status plugin

```bash
pip3 install powerline-status
```

#### 5. Locate powerline-daemon directory (need to wait a while for command to finish running)

```bash
find / 2> /dev/null | grep powerline-daemon
```

Copy the line that ends in `/bin/powerline-daemon` and save it somewhere.

![Alt text](image.png)

#### 6. Locate powerline.sh

```bash
find / 2> /dev/null | grep powerline.sh
```

![Alt text](image-1.png)

Copy the line that ends in `/bash/powerline.sh` and save it somewhere.

#### 7. Open .bashrc

```bash
code ~/.bashrc
```

#### 8. Scroll to bottom of .bashrc and paste the following

```bash
#Powerline
export PATH="PATH:/home/foo/.local/bin/"
export LC_ALL=en_US.utf-8
powerline-daemon -q
POWERLINE_BASH_CONTINUATION=1
POWERLINE_BASH_SELECT=1
source /home/foo/.local/lib/python3.10/site-packages/powerline/bindings/bash/powerline.sh
```

#### 9. Make the following folders

```bash
mkdir -p ~/.config/powerline/colorschemes
mkdir -p ~/.config/powerline/themes/shell
```

#### 10. Copy original ```default.json``` config files into new folder

```bash
cp /home/foo/.local/lib/python3.10/site-packages/powerline/config_files/colorschemes/default.json ~/.config/powerline/colorschemes
```

```bash
cp /home/foo/.local/lib/python3.10/site-packages/powerline/config_files/themes/shell/default.json ~/.config/powerline/themes/shell
```

#### 11. Open colorscheme/default.json

```bash
code ~/.config/powerline/config_files/colorschemes/default.json
```

#### 12. Paste the following in "groups" for git customisation

```json
"gitstatus":                 { "fg": "gray8",           "bg": "gray2", "attrs": [] },
"gitstatus_branch":          { "fg": "gray8",           "bg": "gray2", "attrs": [] },
"gitstatus_branch_clean":    { "fg": "green",           "bg": "gray2", "attrs": [] },
"gitstatus_branch_dirty":    { "fg": "gray8",           "bg": "gray2", "attrs": [] },
"gitstatus_branch_detached": { "fg": "mediumpurple",    "bg": "gray2", "attrs": [] },
"gitstatus_tag":             { "fg": "darkcyan",        "bg": "gray2", "attrs": [] },
"gitstatus_behind":          { "fg": "gray10",          "bg": "gray2", "attrs": [] },
"gitstatus_ahead":           { "fg": "gray10",          "bg": "gray2", "attrs": [] },
"gitstatus_staged":          { "fg": "green",           "bg": "gray2", "attrs": [] },
"gitstatus_unmerged":        { "fg": "brightred",       "bg": "gray2", "attrs": [] },
"gitstatus_changed":         { "fg": "mediumorange",    "bg": "gray2", "attrs": [] },
"gitstatus_untracked":       { "fg": "brightestorange", "bg": "gray2", "attrs": [] },
"gitstatus_stashed":         { "fg": "darkblue",        "bg": "gray2", "attrs": [] },
"gitstatus:divider":         { "fg": "gray8",           "bg": "gray2", "attrs": [] }
```

#### 13. Paste the following in /themes/shell/default.json

```json
{
"function": "powerline_gitstatus.gitstatus",
"priority": 40
}
```


#### 14. Close and open terminal

Should see something like this:

![Alt text](image-2.png)

Original instructions informed to perform 

```bash
source ~/.bashrc
```

but I met PATH problems. Opening and closing terminal launched powerline worked just fine for me.

#### 15. Download git fonts for powerline

```bash
git clone https://github.com/powerline/fonts.git --depth=1 powerline_fonts
```

#### 16. Run installation script in cloned powerline_fonts folder

```bash
./powerline_fonts/install.sh
```

Some fiddling around with the install.sh file might be required to get the installation path correct

More info: <https://askubuntu.com/questions/3697/how-do-i-install-fonts>

#### 17. Change font in terminal settings

![Alt text](image-3.png)

![Alt text](image-4.png)

#### 18. Restart powerline-daemon to make git status appear

```bash
powerline-daemon --replace
```

#### 19. Done

![Alt text](image-5.png)