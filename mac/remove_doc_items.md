# Remove all dock items from a fresh MacOS install

Ever get annoyed having to remove all the items from the MacOS dock one by one after a fresh reinstall? Use dockutil to automate it!

1. Install Homebrew: `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`
2. Install dockutil: `brew install docutil && brew link dockutil`
3. Loop through each dock item and remove it: 
```
for item in $(dockutil --list | cut -f 1); 
  do
  dockutil --remove "$item" --allhomes
done
