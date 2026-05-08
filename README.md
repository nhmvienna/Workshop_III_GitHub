# Workshop III - GitHub

The slides to this workshop can be found [here](https://docs.google.com/presentation/d/1Gpgd5MocTWWqo_unQImQB14VJrkZsUmto1m_VaD_Ii0/edit?slide=id.g112930cb4ee_2_50#slide=id.g112930cb4ee_2_50)

For additional very basic info to the usage of git, see [here](https://GitHub.com/nhmvienna/FirstSteps/blob/main/UNIXBasics/UNIXBasics.md#vii-using-git-for-version-control)

### 1. Git, GitHub and SSH authetication

The first thing you will need to do is to set your Name and GitHub account email to enable syncing to your GitHub cloud.

```bash
git config --global user.name "Your Name"
git config --global user.email "<your@email.com>"
```
Verify your configuration 

```bash
git config --list
```

As a next step, you will need to set up an SSH-key, which GitHub can use to login from your computer to the GitHub account in the cloud. Password authetication is no longer supported. In terminal, you will need to set a new pair of private and public SSH keys

```bash
ssh-keygen -t ed25519 -C "<your@email.com>"
```

This will create two files in the hidden `./ssh/` directory of your home folder

```bash
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
```

Next, whe will start the SSH-agent to organize the SSH-key authentification. Then, add your key

```bash
eval "$(ssh-agent -s)"

## add key
ssh-add ~/.ssh/id_ed25519
```

Finally, you will need to copy your PUBLIC key and set up GitHub SSH authetification on the webpage. Therefore go to the [settings](https://github.com/settings/keys) page of GitHub and navigate to the `SSH and GPG keys` tab. There, click on `New SSH key`.

![key](images/GitHubVSCode/Gitkey1.jpeg)

Come up with a meaningful title, e.g. `VSCode`

Back in the Terminal, you need to get and copy the PUBLIC key. Therefore, display the public key using the `cat` command.

```bash
cat ~/.ssh/id_ed25519.pub
```

This will print the public key to the console. Mark the full string shown in the terminal and right-click copy the string to your clipboard. Now paste the full string in the `Key` field in Github and press `Add SSH key`.

![key](images/GitHubVSCode/Gitkey2.jpg)

Finally, verify that It has worked in the Terminal by typing:

```bash
ssh -T git@github.com

## Sucess!!
Hi capoony! You've successfully authenticated, but GitHub does not provide shell access.
```

### 2. GitHub & VSCode

Before you start, have a quick refresher what VSCode is and how VSCode works, see [here](https://GitHub.com/nhmvienna/FirstSteps/blob/main/VisualStudioCode_basics.md)

##### a) setting up GitHub on VSCode

Find login field on GitHub tab on the right of the VSCode window

![login](images/GitHubVSCode/Login.jpg)
![login2](images/GitHubVSCode/Login2.jpg)

##### b) Clone a repository

```bash
## create GitHub directory in home folder

mkdir ~/github

cd ~/github

## check if your git is set up correctly

git config --global --list

# 1) clone private My1stRepo repository

# then enter the tocken when prompted

git clone https://capoony@GitHub.com/capoony/My1stRep

# 2) clone public repository

git clone https://GitHub.com/nhmvienna/Workshop_III_GitHub
```

See also [here](shell/clone_repository.sh)

Now add the newly cloned folder to the Workspace in VSCode by pressing `File` -> `Add Folder to Workspace...` and select the folder you just cloned.

##### c) Publish a repo on GitHub

Create a new project folder which contains the data that you want to publish

```bash
## create GitHub directory in home folder

mkdir -p ~/github/My2ndRepo/data

cd ~/github/My2ndRepo

## lets add an empty text file in the data folder
touch data/README.md

## lets add a readme file in the main folder
echo '''
# Wow, second Repo 

![GitHub Logo](https://miro.medium.com/v2/resize:fit:620/1*FpEDNFF2CDqpmdkSHXFpmA.jpeg)

:+1:

''' > README.md
```

Now add the newly created folder to the Workspace in VSCode by pressing `File` -> `Add Folder to Workspace...` and select the folder you just created.

Then press `Ctrl+Shift+P` and type publish, or select `Publish to GitHub`

A new /.git folder will appear within the project, which represents the git repository.
New files will appear in green as unstaged (and thus not yet version-controlled) files.

Let's make a new gitignore file, which will tell git to ignore certain files or folders, in this case, we will ignore the data folder

```bash

## add gitignore file
echo '''# ignore data folder
data/
''' > .gitignore

## lets make a second text file in the data folder
echo "This is a second file in the data folder" > data/second_file.txt

## lets make a third text file in the main folder
echo "This is a third file in the main folder" > third_file.txt
```

- Open the source control tab on the left side of the VSCode window, which looks like a branch icon. Therefore use the shortcut `Ctrl+Alt+B` or click on the secondary side bar  icon on the top left side of the VSCode window.

- Now, you can see the changes in the Source Control tab on the left side of the VSCode window.

- Type a brief description of the changes you made in the text box at the top of the Source Control tab.

- Then click on the plus icon next to the file name to stage the changes, or click on the plus icon next to the "Changes" header to stage all changes at once.

- Now you can commit by pressing the `Commit` button, which is also the checkmark icon at the top of the Source Control tab.

- Finally, you can push the changes to GitHub by clicking on the small button with the arrow pointing upwards at the top of the Source Control tab.

#### d) let's check the changes online

```bash
open https://github.com/capoony/My2ndRepo
```

#### e) let's make some additional changes online

- Go to the `README.md` file in the `My2ndRepo` repository on GitHub and click on the pencil icon to edit the file.

- In the sidebar on the right click on the three dots next to the repo name and choose `Fetch` to fetch the changes you made online.

- Now you can see the changes in the Source Control tab on the left side of the VSCode window.

- Pull the changes by clicking on the small button with arrow pointing downwards at the top of the Source Control tab.

#### f) let's make some changes in VSCode

- Go to the `README.md` file in the `My2ndRepo` repository on your local machine and add a new line with the text `new branch`.
Then save the file.

- Now you can see the changes in the Source Control tab on the left side of the VSCode window.

- Create a new branch by clicking on the branch icon at the top of the Source Control tab and selecting `Create Branch...`. Name the branch `new`.

- Now press `Publish Branch` to publish the new branch to GitHub.

- Type a brief description of the changes you made in the text box at the top of the Source Control tab.

- Then click on the plus icon next to the file name to stage the changes, or click on the plus icon next to the "Changes" header to stage all changes at once.

- Now you can commit by pressing the `Commit` button, which is also the checkmark icon at the top of the Source Control tab.

- Finally, you can push the changes to GitHub by clicking on the small button with the arrow pointing upwards at the top of the Source Control tab.
