# Workshop III - GitHub

The slides to this workshop can be found [here](Workshop%20III%20-%20Github.pdf)  
The recordings of the Workshop can be found on the NHM intranet under `I:\Public\mkapun\FrontiersInMolecularSystematics\Workshop_III_GitHub`  
For additional very basic info to the usage of git, see [here](https://GitHub.com/nhmvienna/FirstSteps/blob/main/UNIXBasics/UNIXBasics.md#vii-using-git-for-version-control)

## Index:

1.  [GitHub Desktop](https://GitHub.com/nhmvienna/Workshop_III_GitHub#1-github-desktop)

2.  [GitHub and ATOM](https://GitHub.com/nhmvienna/Workshop_III_GitHub#2-github--atom)

* * *

### 1. GitHub Desktop

a) Obtain GitHub desktop from [here](https://desktop.GitHub.com/)
![GD](images/GithubDesktop/GD.png)

b) Once installed, choose File > Option… to log in to your account

![Options](images/GithubDesktop/image003.png)

![Login](images/GithubDesktop/image002.png)

c) Once successfully logged in, GitHub Desktop will list all your repositories. Pick your previously created 1st repository. Choose the path to where you want to put the files on your computer

![Choose](images/GithubDesktop/image006.png)

d) The overview window shows that there are no current changes to “My1stRep”

![overview](images/GithubDesktop/image005.png)

e) Now click “Show in Explorer”. This will show all the files that GitHub Desktop copied.

![explorer](images/GithubDesktop/image004.png)

f) Double click on README and open with the Editor program. Now you can edit the text and, for example, try some markdown codes.
Then save your changes and go back to GitHub Desktop

![edit](images/GithubDesktop/image001.png)

g) GitHub Desktop shows that README.md was modified and highlights the changes in the right-hand panel.
In the bottom left, you can now add a description and commit the changes

![changes](images/GithubDesktop/image007.png)

h) Once the local changes are committed, you also need to upload these to GitHub. Press “Push origin” on the right hand side. Then you can see your updates on the GitHub page of the repository

![commit](images/GithubDesktop/image009.png)

![updates](images/GithubDesktop/image010.png)

### 2. GitHub & ATOM

Before you start, have a quick refresher what Atom is and how Atom works, see [here](https://GitHub.com/nhmvienna/FirstSteps/blob/main/ATOMbasics.md)

##### a) setting up GitHub on Atom

Find login field on GitHub tab on the right of the Atom window

![login](images/GithubAtom/image001.png)

Get your token by logging into your browser under <https://GitHub.atom.io/login>. Then copy token and paste into empty field in Atom

![token](images/GithubAtom/image002.png)

![token2](images/GithubAtom/image010.png)

##### b) Clone a repository

```bash
## create GitHub directory in home folder

mkdir ~/github

cd ~/github

## check if your git is set up correctly

git config --global --list

# 1) clone private My1stRepo repository

## note that you need your access tocken for that

firefox https://GitHub.atom.io/login

# then enter the tocken when prompted

git clone https://capoony@GitHub.com/capoony/My1stRep

# 2) clone public repository

git clone https://GitHub.com/nhmvienna/Workshop_III_GitHub
```

See also [here](shell/clone_repository.sh)

##### c) Publish a repo on GitHub

Add a new project folder which contains the data that you want to publish, or create a new folder and add it as a project folder

![add](images/GithubAtom/image006.png)

![explorer](images/GithubAtom/image004.png)

Once the Folder appears in the project tab, you can see, that it is neither initialized, i.e. under version control with git, nor published on GitHub

![added](images/GithubAtom/image005.png)

Once you press “initialize”, you can decide where to publish
Please **ALWAYS** use your private account, unless the repo is (1) a software project to be published or (2) a resource for the NHM. By default, it is published public, which may be not what you want!

![publish](images/GithubAtom/image008.png)

A new /.git folder will appear within the project, which represents the git repository.
New files will appear in green as unstaged (and thus not yet version-controlled) files.

![unstaged](images/GithubAtom/image009.png)

Once they are staged, they are ready to be committed

![staged](images/GithubAtom/image011.png)

You need to write a description for every commit, in this case, it is our “initial commit”

![committed](images/GithubAtom/image012.png)

Last, but not least you need to “publish”, which, is very well hidden at the right bottom.
Congrats, now, your repo is online!

![publish](images/GithubAtom/image013.png)

##### d) Make changes to your repo

When you make edits to your files under version control, the changes in the text will be highlighted by vertical bars in the editor and by changes to the color of the filename

![changes](images/GithubAtom/image015.png)

As before, you need to stage the changes and add a description before committing the changes.
Once this is done, you can push the changes, by pressing the same small button as before.

![final](images/GithubAtom/image014.png)
