### Good morning! What you should do when you get to work ###
<pre>
git fetch --prune && git log HEAD..origin/master
</pre>
### Undo all you have done since last commit ###
Very dangerous/delicious - including deleting untracked files and folders (but not ignored files)
<pre>
git reset --hard HEAD && git clean -df
</pre>
### Remove last commit ###
<pre>
git reset --hard HEAD~1
</pre>
### Merge in a feature branch after a rebase and keep the "loop" ###
On master:
<pre>
git merge --no-ff <FEATURE_BRANCH>
</pre>
### Pull in changes from master on the remote server while on a feature branch and rebase that branch on the new master head ###
On feature branch:
<pre>
git pull --rebase origin master
</pre>
### Push feature branch to the remote server ###
<pre>
git push -u origin <FEATURE_BRANCH>
</pre>
### Remove feature branch from the remote server ###
<pre>
git push origin --delete <FEATURE_BRANCH>
</pre>
### Add changes to latest commit and keep the original commit message ###
<pre>
git commit --amend --no-edit
</pre>
### Add changes to latest commit and edit the original commit message ###
<pre>
git commit -a --amend
</pre>
### Exit the VIM editor (default GIT editor) ###
<pre>
:q!
</pre>
### Show branches not merged into master ###
<pre>
git branch --no-merged master
</pre>
### Show where a repo was cloned from ###
<pre>
git remote -v
</pre>
or
<pre>
git remote show origin
</pre>
### List tags ordered by creation date ###
<pre>
git tag --sort=-creatordate
</pre>
### Create tag and push ###
<pre>
git tag -a <TAG_NAME> -m "<TAG_MESSAGE>" && git push --tags
</pre>
### Delete local tag ###
<pre>
git tag --delete <TAG_NAME>
</pre>
### Delete remote tag ###
<pre>
git push --delete origin <TAG_NAME>
</pre>
### List all tags with annotations ###
<pre>
git tag -n9
</pre>
### List all tags in cronological order ###
<pre>
git for-each-ref --sort=creatordate --format '%(refname)' refs/tags
</pre>
### Rename branch ###
<pre>
git branch -m <OLD_NAME> <NEW_NAME>
</pre>
or rename the current branch
<pre>
git branch -m <NEW_NAME>
</pre>
### Stash away changes (and remove them from working dir) ###
<pre>
stash
</pre>
### Also stash away unstaged (k) and new (u) files ###
<pre>
git stash -k -u
</pre>
### Get stashed files back ###
<pre>
git stash pop
</pre>
### Force push master to the remote server ###
<pre>
git push --force
</pre>

### Force push branch (e.g. a detached head) to the master branch on the remote server ###
<pre>
git push origin +<HASH_OF_COMMIT_TO_BE_NEW_MASTER>:master
</pre>
then
<pre>
git reset --hard origin/master
</pre>
to update the local master
### Change a remote's URL ###
<pre>
git remote set-url <REMOTE_NAME> <NEW_URL>
</pre>
for instance
<pre>
git remote set-url origin http://domain.com:8080/git/Repo/test.git
</pre>
Remember you can use git remote -v to check which remotes you have

### Remove branches you have been tracking, but which have been deleted from the remote ###
<pre>
git remote prune origin
</pre>

### Restore a single file from another commit ###
<pre>
git checkout <HASH_OF_COMMIT> -- "<RELATIVE_PATH_TO_FILE>"
</pre>

### Check out a single file from another branch and rename it ###
Works best if already in the correct folder where the file that should be checked out is in the local branch, and where the checked out copy should be stored.
<pre>
git show <OTHER_BRANCH>:./<FILE_NAME> > <OTHER_FILE_NAME>
</pre>

### Set another editor as default editor ###
Notepad++
<pre>
git config core.editor "'C:\Program Files\Notepad++\notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
</pre>
Notepad2
<pre>
git config core.editor "'C:\Program Files\TortoiseGit\bin\notepad2.exe'"
</pre>
### Edit global config in notepad ###
<pre>
git config --edit --global
</pre>
### Create alias ###
<pre>
git config --global alias.co checkout
</pre>
### Create alias with multiple commands or add options ###
Edit the global config. Add extra lines in the [alias] section, e.g.:
<pre>
[alias]
	fs = !git fetch && git status
	pr = pull --rebase
</pre>
The global gitconfig can usually be found here:
<pre>
C:\Users\<username>\.gitconfig
</pre>
### Instruct GIT to store credentials for this repo ###
<pre>
git config credential.helper store
</pre>

### Create list of commit info between commits ###
<pre>
git log <TAG_OR_HASH_OF_FIRST_COMMIT>..<TAG_OR_HASH_OF_SECOND_COMMIT>
</pre>

### Dump list of commit messages between commits to a file only showing the body ###
<pre>
git log <TAG_OR_HASH_OF_FIRST_COMMIT>..<TAG_OR_HASH_OF_SECOND_COMMIT> --format="%B" > log.txt
</pre>

### Ignore changes to a specific file (e.g. the build date file) ###
<pre>
git update-index --assume-unchanged Assets/Resources/Temp/BuildDate.bytes
</pre>

### Show branches (including on server) matching something ###
<pre>
git branch -a --list '*match*'
</pre>

### Show latest commit hash ###
<pre>
git rev-parse HEAD
</pre>

### Pull to master from local folder ###
<pre>
git pull path/to/local/folder master
</pre>

### Undo last commit (but keep changes) ###
<pre>
git reset --soft HEAD~
</pre>



= Configuration =
### The "domain.com" domain ###
Make sure domain.com is in your hosts file. On Windows this can be achived by running this .bat file as administrator:

<pre>@ECHO OFF
SET NEWLINE=^& echo.
FIND /C /I "domain.com" %WINDIR%\system32\drivers\etc\hosts
IF %ERRORLEVEL% NEQ 0 ECHO %NEWLINE%^123.123.123.123 domain.com>>%WINDIR%\System32\drivers\etc\hosts</pre>

### Installing Git the first time ###
Please select the option "Checkout as-is, commit as-is". Contrary to common belief, Windows '''does''' support text files with LF [[Line-Endings]]. You never need the CR character for anything. Run these two commands before downloading ("cloning") any repos:
<pre>
git config --global core.autocrlf input
git config --global core.eol lf
git lfs install
</pre>


[[Category:Development]]
[[Category:Tips & Tricks]]
